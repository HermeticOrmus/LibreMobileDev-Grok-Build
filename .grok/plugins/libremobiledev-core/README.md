# libremobiledev-core (v0 plugin stub, kept as a dogfood copy)

This was the v0 plugin bundle. It had no manifest and no skills, so it bundled nothing: Grok saw it only as a project plugin with one agent, the stub orchestrator. It stays as the dogfood copy of `stubs/agents/mobile-orchestrator.md` (the two files must match; CI checks it).

The installable plugin is now [`plugins/libre-mobiledev-grok/`](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/tree/main/plugins/libre-mobiledev-grok), with its own manifest. Install it with `grok plugin marketplace add HermeticOrmus/LibreMobileDev-Grok-Build` and `grok plugin install libre-mobiledev-grok@LibreMobileDev-Grok-Build`.

The melted skills now live in that plugin's `skills/`; the stubs live in `stubs/skills/`. Dogfood copies of both: `.grok/skills/`.

Melted in the pack (use those bodies): `mobile-a11y`, `app-store-checklist`, `offline-first`. The other five skills and this plugin wrapper remain stubs. Honest table: [docs/DEPTH_MATRIX.md](../../../docs/DEPTH_MATRIX.md).
