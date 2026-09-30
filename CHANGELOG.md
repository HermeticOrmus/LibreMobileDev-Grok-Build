# Changelog

## [1.0.0] - 2026-09-30

The Grok edition: one marketplace add brings the Grok-native skills plus the LibreMobileDev pack, pinned by commit. Every crack this release found and sealed is in [LEDGER.md](./LEDGER.md).

### Added

- `plugins/libre-mobiledev-grok/`: the three melted skills (`mobile-a11y`, `app-store-checklist`, `offline-first`) as an installable Grok plugin with `.grok-plugin/plugin.json` (version 1.0.0).
- `.grok-plugin/marketplace.json` (`libre-mobiledev-grok`): the Grok-native plugin, then all 21 LibreMobileDev-Claude-Code plugins as remote entries pinned to commit `87caa9f`. The optional `libre-mobiledev-hooks` plugin installs too; its hooks are unverified inside a Grok session.
- `scripts/pin-pack.sh`: moves every pack entry to the pack's current main HEAD, adds new pack plugins, drops removed ones, and prints the diff. `--check` fails when the pack's plugin set changed.
- `.github/workflows/validate.yml`: validates the plugin, checks the dogfood copies, checks every pinned commit is reachable, checks the pack plugin names, and installs every entry in a clean `GROK_HOME`.
- Issue forms for feedback, routing misses and plugin proposals, with the `feedback`, `routing-miss` and `plugin-proposal` labels.
- `LEDGER.md`, the kintsugi ledger: 11 cracks sealed, 5 open.

### Changed

- The melted skills moved from `skills/` to `plugins/libre-mobiledev-grok/skills/`. The stubs moved to `stubs/skills/` and the orchestrator from `AGENTS/` to `stubs/agents/`; none of them install. Each stub names the pack plugin that holds the real depth, and its description starts "Stub cue".
- Install is `grok plugin marketplace add HermeticOrmus/LibreMobileDev-Grok-Build`, then `grok plugin install <plugin>@LibreMobileDev-Grok-Build`. README, QUICK_START, AGENTS, CONTRIBUTING, DEPTH_MATRIX and MELT_RULES follow the new layout.
- README header follows the Ormus GitHub standard; the Depth table counts what installs.
- `.grok/skills/` stays as the dogfood copy of the plugin skills and the stubs, and `.grok/plugins/libremobiledev-core/` stays as the dogfood copy of the stub orchestrator. CI keeps both in sync.
- What a 0.1.0 user must change: delete the skill folders you copied from `skills/` (the stubs among them are cues, not skills), then install through the marketplace. If you installed the repo root directly, uninstall that plugin; the root holds no skills now.

### Fixed

- 6 relative links in the dogfood copies that resolved inside `.grok/` now point at the real files.
- The `push-notifications` and `react-native-patterns` stubs' frontmatter is valid YAML (quoted descriptions).

## [0.1.0] — 2026-09-20

### Changed

- Melted `skills/mobile-a11y/SKILL.md`, `skills/app-store-checklist/SKILL.md`, and `skills/offline-first/SKILL.md` into usable Grok skills (when-to-use, checks, examples, output shape). Dogfood copies under `.grok/skills/` match.
- Rewrote [QUICK_START.md](./QUICK_START.md) for a clean-machine install (<5 min) with paths that exist in this repo.
- Updated [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md): 3 melted (L3–L4), 5 stub skills, 1 stub agent. No Claude inventory counts.
- Suite footers on README, QUICK_START, and AGENTS.md now link Reality OS plus the sibling Libre*-Grok-Build packs.

## [0.0.1] — 2026-09-19

### Added

- Public scaffold for LibreMobileDev-Grok-Build (v0 stubs).
- Stub SKILL.md for first skills + suite orchestrator agent.
- README, LICENSE (MIT), GOLD_HAT, QUICK_START, CONTRIBUTING, SECURITY.
- Depth matrix + melt rules docs.

### Notes

- Honest stubs — not fake upstream depth counts. Melt next.
