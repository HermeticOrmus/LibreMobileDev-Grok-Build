---
name: offline-first
description: Offline-first sync — local source of truth, outbox, named conflict policy, backoff, offline UX. Use when a mobile feature must work without a network.
---

# Offline First

The device is the product. Network is an optimization. If the primary write dies when the radio dies, the design is online-only — say so.

Gold Hat: keep the person's data on their device and teach the conflict rule in language they can reuse. Silent "server wins" that deletes an offline edit extracts. A named policy they can predict empowers.

## When to use

- A create / edit / complete action that people will do in a tunnel or airplane
- Adding a backend to an existing local list
- Sync bugs (dupes, lost edits, stuck spinners)
- Before you invent a third cache

Do not use this for analytics-only or strictly live-only features (payments confirmation, ticket scan) — say **online-required** and stop. Hand leftovers to still-stub skills: `push-notifications` (wake-to-sync), `deep-linking` (open a record that is not on disk yet), `mobile-perf` (queue size / main-thread I/O). Call the stub; do not invent its depth.

## Operating steps

1. **Name the records.** Which objects must be readable and writable with no radio? If none, this skill does not apply.
2. **Declare the source of truth.** Local store is authoritative for those records until a sync ack. UI reads the local store, not a pending HTTP response.
3. **Install an outbox.** Every mutating intent is an idempotent item (`clientMutationId` or durable op id) with state `pending | in-flight | acked | failed`.
4. **Name the conflict policy** before writing merge code. One policy per record type. Write it where the next engineer will see it.
5. **Show offline.** Banner or status that is honest. Failed items are retryable. Never block the primary write on "connecting…".

Stop if you cannot name the conflict policy. Ask. Implicit last-write-wins is how edits vanish.

## Checks (measurable)

### Local source of truth

| Check | Pass | Fail |
|-------|------|------|
| Read path | List/detail render from disk (SQLite/Drift/Room/Core Data/Watermelon/…) | Blank screen until `GET` returns |
| Write path | Insert/update local, then enqueue | `await api.create()` then write local |
| Identity | Client-generated id (UUID) at create time | Server id required before the row exists |

### Outbox and idempotency

| Check | Pass | Fail |
|-------|------|------|
| Durable queue | Ops survive process death | In-memory array of "pending POSTs" |
| Idempotency | Same op id cannot create two server rows | Retry after 201 creates a duplicate |
| Backoff | Transient network → retry with cap; 4xx (except 409) does not tight-loop | Infinite immediate retry on airplane mode |
| Ack | Local row marked synced only after a definite server ack | Optimistic "synced" on request start |

### Conflict policy (pick one, write it down)

| Policy | Use when | Honest cost |
|--------|----------|-------------|
| Last-write-wins (timestamp) | Single user, one record type, clocks close enough | Concurrent edits: one disappears |
| Server wins | Server is canonical; local is a cache | Offline edits can be dropped — must tell the user |
| Client wins | Local action is always valid (drafts) | Overwrites other devices |
| Field merge | Independent fields (title vs done) | Needs a base version; still fails on the same field |
| CRDT / op log | Multi-user same document | High complexity; do not pretend you have one |

| Check | Pass | Fail |
|-------|------|------|
| Named | Policy is a comment, ADR, or type name next to the merge | "we just upsert" |
| User-visible loss | If a policy can drop an edit, the UI says so | Silent revert on next sync |

### Offline UX

| Check | Pass | Fail |
|-------|------|------|
| Primary action | Works at radio-off | Save disabled until online |
| Status | Pending / failed / synced is visible per item or toolbar | Infinite spinner |
| Replay | Failed op can be retried without retyping | Error toast, data gone |

## Worked example — add a task in a tunnel

Job: a commuter adds "Buy rice" on the train. Primary action: Add.

Weak:

```text
onSubmit → POST /tasks → setState(tasks)
```

No local row, no op id, spinner until 201, duplicate on retry.

Stronger (policy: last-write-wins on `updatedAt`, single-user list):

```text
onSubmit:
  id = uuid()
  write Task(id, title, updatedAt=now, sync=pending)
  enqueue Op(id=uuid(), type=upsertTask, body=task, idempotencyKey=id)
  render from local query
onNetwork:
  drain outbox; backoff on IO
  409 → fetch server row → keep the newer updatedAt; if local lost, mark "replaced by other device"
```

- **SoT:** the list is the local query. The train ride still shows "Buy rice".
- **Outbox:** process death does not lose the op.
- **Idempotency:** `idempotencyKey = task.id` so a double drain cannot create two "Buy rice".
- **Conflict:** LWW is named. Two-device edit of the same title can drop one — acceptable only because this product is single-user. If it becomes shared, stop and pick field-merge or an op log; do not "just upsert" harder.
- **UX:** row shows pending; failed shows Retry.

Three concrete fixes if you only have the weak path: (1) UUID + local insert first, (2) durable outbox with idempotency key, (3) name LWW in one comment and a pending chip — then leave push-wake and cold-start jank to the stub skills.

## Output shape

```markdown
## Job
[who / records / primary write]

## Source of truth
[local store + read/write path] — [or: online-required, stop]

## Outbox
[where / idempotency key / states]

## Conflict
[policy per record type] — [what the user sees if they lose]

## Findings
1. **[Critical|High|Medium|Low] — [check].** [where] [current] → [needed]
2. …

## Fixes now
1. …
2. …
3. …

## Teach
[one reusable sentence]

## Leftovers
- [stub skill] — [what you did not pretend to finish]
```

Severity: **Critical** is data loss or a primary write that requires the network. **High** is dupes or silent revert. **Medium** is missing pending UI or unnamed policy on a low-stakes record. **Low** is naming/doc. Empty findings are allowed.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
