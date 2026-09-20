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

Dogfood copies of every skill live at `.grok/skills/<name>/SKILL.md` and must match `skills/<name>/SKILL.md`.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling Libre*-Grok-Build packs: [README suite footer](../README.md).
