---
name: app-store-checklist
description: App Store and Play submit gate — privacy labels, screenshots, review notes, crash-free, rollback. Use before you press Submit, not as keyword-stuffing theater.
---

# App Store Checklist

A **release gate** for App Store Connect and Google Play Console. The job is "will review accept this build, and can we roll it back?" — not ASO ranking.

Gold Hat: put the submitter in control of every claim on the listing. Hidden tracking, a fake demo account, or "we'll fix privacy after approval" extracts. Teaching the gate so they can run it next time empowers.

## When to use

- First submit or a non-trivial version
- New permission, SDK, login, IAP, or data type
- After a rejection, before you resubmit
- Release-candidate cut (pair a11y first: `mobile-a11y`)

Do not use this as a growth / keyword playbook. Upstream Claude ASO patterns are proof that listing copy exists — they are not this skill. Do not invent conversion scores. Hand leftovers to still-stub skills: `mobile-perf` (startup/jank/crash), `push-notifications` / `deep-linking` (payload and URL review). Call the stub; do not invent its depth.

## Operating steps

1. **Name the binary.** Bundle / application id, version + build, stores, countries, what changed since last live.
2. **Walk the gates** below. Each row is pass, fail, or **unverified** (you did not open Console / Connect / the build).
3. **Write review notes** a stranger can follow. Demo account, not a real user. No secrets in the notes, the skill, or the chat.
4. **Name the rollback.** Phased release, previous build keep, Play staged rollout halt. If there is no rollback, that is a finding.
5. **Teach one sentence.** The rule the next submit reuses.

Stop if you do not know what the binary collects. Ask. Guessing a privacy nutrition label is extraction and a rejection.

## Gates (measurable)

### Identity and completeness

| Check | Pass | Fail |
|-------|------|------|
| Same app | Bundle id / application id matches the listing | Debug id or a second "copy" app |
| Version | Marketing version + build increment; what-changed is true | Placeholder "Bug fixes" when you added tracking |
| Completeness | Every required metadata field filled for the locales you ship | Lorem, TODO, empty subtitle, broken preview |

Guideline 2.1 (incomplete) is still the high-volume reject. If a flow is unfinished, do not submit it.

### Privacy, tracking, and deletion

Reviewers compare the binary to the form. Mismatch is a reject.

| Check | Pass | Fail |
|-------|------|------|
| Nutrition / Data safety | Every collected type and purpose matches the code and SDKs | SDK collects advertising id; form says "no data" |
| Purpose strings | Camera, location, contacts, photos, tracking: real usage text | `"$(PRODUCT_NAME) needs this"` or unused permission |
| ATT / ads | Tracking prompt only if you track; copy matches the form | Prompt with no tracking, or tracking with no prompt |
| Account deletion | In-app delete if you have accounts (store rules) | Delete-via-email-only, or no delete |
| Secrets | Review notes use a dedicated demo login | Production password, API key, or user PII in notes |

Never paste real credentials into this skill's examples or the session. Say `demo@example.com` / a vault pointer the human already owns.

### Screenshots and listing assets

Look up **current** required device classes in Connect / Play for the devices you support. Pixel tables go stale; do not invent sizes.

| Check | Pass | Fail |
|-------|------|------|
| Required classes | One set per required phone/tablet class you claim | Missing 6.7"/6.9" iPhone or Play phone set |
| Honest UI | Screenshots are this binary, this locale | Mockups of features that are not in the build |
| Benefit, not chrome | First frame shows the job | Unannotated settings dump |
| Play feature graphic | Present if Play requires it for your listing | Missing 1024×500-class graphic when Console blocks submit |

### Review notes (what a stranger can do)

Write steps, not slogans.

```text
What to review: [one primary path]
Demo account: [vault name or demo@ — not a password here]
IAP / subscriptions: [how to reach, how not to get charged]
Permissions: [which prompt appears, why]
Known limits: [offline, region, hardware]
```

Fail: "just tap around." Fail: pasting a production token. Fail: hiding a login behind an unstated debug gesture.

### Crash-free and rollback

| Check | Pass | Fail |
|-------|------|------|
| Gate | RC meets your crash-free or ANR bar on the devices you ship | "We'll watch it in prod" with no number |
| Symbolication | Crash reports will be readable | dSYM / Play mapping file missing, unverified |
| Rollback | Phased / staged; previous live build retained | 100% flip with no prior binary |
| Store flags | Age rating, export, encryption answers match the app | Copy-pasted yes/no you did not check |

`mobile-perf` (stub) owns startup and jank budgets. Here you only record whether a ship bar exists and whether this RC met it.

## Worked example — first iOS+Play submit

Job: ship 1.0 of a habit tracker that uses an account and optional camera for a journal photo.

Weak notes: "Looks good. Login is the one we use internally." Privacy form: no data collected. Screenshots: Figma, not the RC. No phased release.

Stronger (abridged):

```markdown
## Binary
com.example.habits 1.0.0 (12) — iOS App Store + Play production. New: account, camera journal.

## Gates
1. **Critical — privacy.** Camera permission is in the binary; Data safety / nutrition omitted photos.
   Remediation: declare photos + purpose; purpose string states journal only.
2. **Critical — review notes.** Internal login is a secret. Remediation: demo account in the team vault; notes name the vault item, not the password.
3. **High — completeness.** Account delete is email-only. Remediation: in-app delete before submit.
4. **High — assets.** Screenshots are mockups. Remediation: capture RC on required device classes.
5. **Medium — rollback.** Planned 100% flip. Remediation: iOS phased + Play 10% staged; keep 0.0 TestFlight.

## Review notes (no secrets)
Primary path: sign in with the demo account → add a habit → add a journal photo → complete today.
Demo: vault item "store-review-demo" (email only in notes).
Camera: prompt on first journal photo; deny still allows text journal.
IAP: none in 1.0.

## Teach
The form must match the binary; the notes must not contain the password.
```

## Output shape

```markdown
## Binary
[id / version / stores / what changed]

## Gates (severity-ranked)
1. **[Critical|High|Medium|Low] — [gate].** [evidence] → [remediation]
2. …

## Review notes
[stranger steps; demo identity without secrets]

## Rollback
[phased / staged / previous build / halt]

## Teach
[one reusable sentence]

## Leftovers
- [stub skill] — [what you did not pretend to finish]
```

Severity: **Critical** is a likely reject or a privacy lie. **High** is a missing required asset, no delete, or no demo path. **Medium** is rollback or crash-bar debt. **Low** is copy polish. Unverified stays unverified.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
