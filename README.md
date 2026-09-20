# LibreMobileDev-Grok-Build

**Mobile (Flutter / RN / native) skills for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)** — ported and melted from [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code), not a dumb copy.

> Status: **public v0** — three skills melted (`mobile-a11y`, `app-store-checklist`, `offline-first`); the rest are honest stubs. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Why this exists

Mobile is offline, store-gated, and gesture-native. LibreMobileDev owns that job on Claude Code. Grok Build needs the same *job* with Grok-native skills, `.grok/`, and truth-seeking voice. This repo counts only what it has melted.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md) for clone, dogfood, project-local, and user-global paths.

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git
cd LibreMobileDev-Grok-Build
# Dogfood: .grok/skills/ already has the skill bodies.
# Other project: cp -R skills/* /path/to/your-mobile-project/.grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth (honest)

| Artifact | This repo now | Upstream Claude |
|----------|---------------|-----------------|
| Skills | 3 melted (L3–L4) + 5 stubs (L1) | Proof the job exists; not our inventory |
| Agents | 1 stub (`mobile-orchestrator`) | Proof the job exists; not our inventory |
| Plugins | 1 core bundle stub | Proof the job exists; not our inventory |

Do not paste Claude plugin/agent/command totals here. Update [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) when something melts.

## Skills

| Skill | Status | Job |
|-------|--------|-----|
| mobile-a11y | melted | VoiceOver/TalkBack, targets, contrast, dynamic type |
| app-store-checklist | melted | Submit gate: privacy, screenshots, review notes, rollback |
| offline-first | melted | Local source of truth, outbox, named conflict policy |
| flutter-patterns | stub | Flutter composition, state, navigation, platform channels |
| react-native-patterns | stub | RN navigation, native modules, New Architecture cues |
| mobile-perf | stub | Startup, jank, memory, binary size budgets |
| push-notifications | stub | Permissions, payloads, deep-link targets, quiet hours |
| deep-linking | stub | Universal links / app links / custom schemes |

Agent: `AGENTS/mobile-orchestrator.md` — stub coordinator for a full suite pass.

## Layout (Grok Build)

```
skills/                 # canonical SKILL.md bodies
AGENTS/                 # suite agents
docs/                   # DEPTH_MATRIX, MELT_RULES
.grok/skills/           # dogfood copy of skills/ (keep in sync)
.grok/plugins/          # optional plugin bundle stub
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

This pack: teach the a11y rule, the store gate, and the conflict policy so the person can run them next time. Do not hide a blocker to ship faster. Do not put secrets in review notes or examples.

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreMobileDev-Grok-Build](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
