# libre-mobiledev-grok

The Grok-native layer of [LibreMobileDev-Grok-Build](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build): three skills melted for Grok Build.

| Skill | Job |
|-------|-----|
| `mobile-a11y` | VoiceOver/TalkBack, targets, contrast, dynamic type |
| `app-store-checklist` | Submit gate: privacy, screenshots, review notes, rollback |
| `offline-first` | Local source of truth, outbox, named conflict policy |

## Install

```bash
grok plugin marketplace add HermeticOrmus/LibreMobileDev-Grok-Build
grok plugin install libre-mobiledev-grok@libre-mobiledev-grok
```

The same marketplace offers every LibreMobileDev-Claude-Code plugin, pinned by commit.

The stubs (`flutter-patterns`, `react-native-patterns`, `mobile-perf`, `push-notifications`, `deep-linking`) and the stub orchestrator are not part of this plugin. They live in [`stubs/`](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/tree/main/stubs), and each names the pack plugin with the real depth. Honest table: [docs/DEPTH_MATRIX.md](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/blob/main/docs/DEPTH_MATRIX.md).

Gold Hat: [GOLD_HAT.md](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/blob/main/GOLD_HAT.md)
