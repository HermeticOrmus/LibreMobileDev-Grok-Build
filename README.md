# LibreMobileDev-Grok-Build

**Mobile (Flutter / RN / native) skills for Grok Build** — ported and melted from [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code), not a dumb copy.

> Status: **v0 public scaffold** — honest stubs. Melt depth next.

## Why this exists

Mobile is offline, store-gated, and gesture-native. LibreMobileDev owns Flutter/RN patterns, offline-first, push, deep links, a11y — melted for Grok Build from LibreMobileDev-Claude-Code.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md).

```bash
mkdir -p .grok/skills
cp -R skills/* .grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth matrix (honest)

| Artifact | v0 scaffold | Upstream Claude (proof) |
|----------|-------------|-------------------------|
| Skills (melted bodies) | 8 stubs → fill next | see upstream suite |
| Agents | 1 (`mobile-orchestrator`) | upstream agents |

Counts on the right are **upstream proof**, not this repo's claim until melted.

## First skills

| Skill | Job |
|-------|-----|
| flutter-patterns | Flutter composition, state, navigation, platform channels |
| react-native-patterns | RN patterns: navigation, native modules, New Architecture cues |
| offline-first | Offline-first sync, queues, conflict policy |
| mobile-perf | Startup, jank, memory, binary size budgets |
| push-notifications | Push: permissions, payloads, deep-link targets, quiet hours |
| deep-linking | Universal links / app links / custom schemes — routing safely |
| mobile-a11y | Mobile accessibility: VoiceOver/TalkBack, hit targets, contrast |
| app-store-checklist | App Store / Play submit checklist — privacy, screenshots, review notes |

Agent: `AGENTS/mobile-orchestrator.md` — full suite pass.

## Layout (Grok Build)

```
skills/                 # install into .grok/skills or ~/.grok/skills
AGENTS/                 # suite agents
.grok/plugins/          # optional plugin bundle
docs/                   # DEPTH_MATRIX, MELT_RULES
```

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- Sibling: [LibreUIUX-Grok-Build](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [LibreSessionFlow-Grok-Build](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [LibreGEO-Grok-Build](https://github.com/HermeticOrmus/LibreGEO-Grok-Build)
- Skills packs: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
