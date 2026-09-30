# Depth matrix

Update this table when melting. Status words mean what they say:

| Status | Meaning | Depth |
|--------|---------|-------|
| stub | Thin cue only. Usable as a reminder, not a playbook. | L1 |
| melted | Real Grok skill: when-to-use, steps, measurable checks, example, output shape. | L3–L4 |

L5 (scripts, fixtures, automated gates) is not claimed. Never copy Claude plugin / agent / command totals into this inventory. Upstream [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code) is proof that the *job* exists, not a count this repo has earned.

| ID | Kind | Status | Source (Claude, for melt) | Notes |
|----|------|--------|---------------------------|-------|
| mobile-a11y | skill | melted | plugins/accessibility-mobile | Reader tree, targets, contrast (measure or unverified), example. No `/10` score. |
| app-store-checklist | skill | melted | plugins/app-store-optimization (submit gold only) | Release gate: privacy, assets, review notes, rollback. Not ASO keyword theater. |
| offline-first | skill | melted | plugins/offline-first | Local SoT, outbox, named conflict, offline UX. No framework dump. |
| flutter-patterns | skill | stub | plugins/flutter-development | Composition cue only. |
| react-native-patterns | skill | stub | plugins/react-native | Nav / native-module cue only. |
| mobile-perf | skill | stub | plugins/mobile-performance | Budget cue only. |
| push-notifications | skill | stub | plugins/push-notifications | Permission / payload cue only. |
| deep-linking | skill | stub | plugins/deep-linking | URL / fallback cue only. |
| mobile-orchestrator | agent | stub | suite coordinator | Routes to skills; not a melted specialist. |

This repo now: **3 melted skills**, **5 stub skills**, **1 stub agent**.

Dogfood copies of every skill live at `.grok/skills/<name>/SKILL.md` and must match their source: `plugins/libre-mobiledev-grok/skills/<name>/SKILL.md` for melted skills, `stubs/skills/<name>/SKILL.md` for stubs. CI checks it.

## v1.0.0: where each row lives

Melted skills install as the `libre-mobiledev-grok` plugin. Stubs stay in `stubs/` and never install; each names the pack plugin that holds the real depth. The 21 pack plugins install from the same marketplace, pinned to one commit of [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code) (see `.grok-plugin/marketplace.json`). They are installed depth, not this repo's inventory.

| ID | Lives at | Installs | Real depth, installed by this marketplace |
|----|----------|----------|-------------------------------------------|
| mobile-a11y | `plugins/libre-mobiledev-grok/skills/mobile-a11y/` | yes, in `libre-mobiledev-grok` | this skill |
| app-store-checklist | `plugins/libre-mobiledev-grok/skills/app-store-checklist/` | yes, in `libre-mobiledev-grok` | this skill |
| offline-first | `plugins/libre-mobiledev-grok/skills/offline-first/` | yes, in `libre-mobiledev-grok` | this skill |
| flutter-patterns | `stubs/skills/flutter-patterns/` | no | `flutter-development` |
| react-native-patterns | `stubs/skills/react-native-patterns/` | no | `react-native` |
| mobile-perf | `stubs/skills/mobile-perf/` | no | `mobile-performance` |
| push-notifications | `stubs/skills/push-notifications/` | no | `push-notifications` |
| deep-linking | `stubs/skills/deep-linking/` | no | `deep-linking` |
| mobile-orchestrator | `stubs/agents/mobile-orchestrator.md` | no | a specialist agent in each pack plugin |

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling Libre*-Grok-Build packs: [README suite footer](../README.md).
