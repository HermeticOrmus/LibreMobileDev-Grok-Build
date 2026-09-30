<p align="center">
  <img src="https://ormus.solutions/mascot/pixellab_liquid_to_portal.gif" alt="LibreMobileDev Grok Build" width="128" style="image-rendering: pixelated;" />
</p>

<h1 align="center">LibreMobileDev Grok Build</h1>

<p align="center">
  <em>Mobile in your Grok Build session: accessibility, store-gate and offline-first skills melted for Grok, plus the LibreMobileDev pack by pinned commit</em>
</p>

<p align="center">
  <a href="https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/stargazers"><img src="https://img.shields.io/github/stars/HermeticOrmus/LibreMobileDev-Grok-Build?style=flat-square&color=aa8142" alt="Stars" /></a>
  <a href="https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/blob/main/LICENSE"><img src="https://img.shields.io/github/license/HermeticOrmus/LibreMobileDev-Grok-Build?style=flat-square&color=aa8142" alt="License" /></a>
  <a href="https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/commits"><img src="https://img.shields.io/github/last-commit/HermeticOrmus/LibreMobileDev-Grok-Build?style=flat-square&color=aa8142" alt="Last Commit" /></a>
  <img src="https://img.shields.io/badge/Mobile-aa8142?style=flat-square&logo=flutter&logoColor=white" alt="Mobile" />
  <img src="https://img.shields.io/badge/Grok_Build-aa8142?style=flat-square&logo=x&logoColor=white" alt="Grok Build" />
</p>

---

**Mobile (Flutter / RN / native) skills for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)** — ported and melted from [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code), not a dumb copy.

> Status: **v1.0.0**. The three melted skills (`mobile-a11y`, `app-store-checklist`, `offline-first`) install as the `libre-mobiledev-grok` plugin, and all 21 LibreMobileDev-Claude-Code plugins install beside them from the same marketplace, pinned by commit. The five stubs stay in `stubs/` and do not install. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) and the [kintsugi ledger](./LEDGER.md).

## Why this exists

Mobile is offline, store-gated, and gesture-native. LibreMobileDev owns that job on Claude Code. Grok Build needs the same *job* with Grok-native skills, `.grok/`, and truth-seeking voice. This repo counts only what it has melted.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md) for the marketplace, dogfood, and copy paths.

```bash
grok plugin marketplace add HermeticOrmus/LibreMobileDev-Grok-Build
grok plugin install libre-mobiledev-grok@libre-mobiledev-grok
# Any pack plugin, pinned by commit, for example:
grok plugin install flutter-development@libre-mobiledev-grok
grok plugin list
```

[QUICK_START.md](./QUICK_START.md) has a loop that installs every entry.

The pack's optional `libre-mobiledev-hooks` plugin installs too; whether its hooks fire inside a Grok session is unverified ([LEDGER.md](./LEDGER.md)).

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth (honest)

| Artifact | This repo now | Installed from the pack |
|----------|---------------|-------------------------|
| Skills | 3 melted, in the `libre-mobiledev-grok` plugin; 5 stubs in `stubs/skills/`, not installed | The skills inside the 21 pack plugins |
| Agents | 1 stub (`mobile-orchestrator`) in `stubs/agents/`, not installed | A specialist agent in each pack plugin except the hooks plugin |
| Plugins | 1 (`libre-mobiledev-grok`, v1.0.0) | 21 of 21, pinned by commit in `.grok-plugin/marketplace.json`, including the optional `libre-mobiledev-hooks` |

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

The melted skills install as the `libre-mobiledev-grok` plugin. The stubs live in `stubs/skills/` and do not install; each one names the pack plugin that holds the real depth, and [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) maps them all.

Agent: `stubs/agents/mobile-orchestrator.md`, the stub coordinator for a full suite pass. It does not install.

One name now exists twice: the pack's `accessibility-mobile` plugin has a `/mobile-a11y` command. Call the Grok-native skill by its qualified name, `libre-mobiledev-grok:mobile-a11y` ([LEDGER.md](./LEDGER.md)).

## Layout (Grok Build)

```
.grok-plugin/marketplace.json       # marketplace: the Grok-native plugin, then the pack's plugins by pinned commit
plugins/libre-mobiledev-grok/       # the Grok-native plugin (manifest in .grok-plugin/plugin.json)
  skills/                           # the melted SKILL.md bodies (canonical)
stubs/skills/                       # stub cues; not installed; each names the pack plugin with the depth
stubs/agents/                       # the stub orchestrator; not installed
scripts/pin-pack.sh                 # re-pins the pack entries to the pack's main HEAD
docs/                               # DEPTH_MATRIX, MELT_RULES
LEDGER.md                           # kintsugi ledger: the cracks and their seals
.grok/skills/                       # dogfood copy of the plugin skills and the stubs (CI keeps it in sync)
.grok/plugins/libremobiledev-core/  # v0 bundle stub, kept as the dogfood copy of the stub orchestrator
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

This pack: teach the a11y rule, the store gate, and the conflict policy so the person can run them next time. Do not hide a blocker to ship faster. Do not put secrets in review notes or examples.

## Kintsugi ledger

[LEDGER.md](./LEDGER.md) lists every crack found in the v0 edition, the evidence, and the seal this release put on it. Open cracks stay open in plain sight until someone seals them.

## Feedback

Tell us what worked and what is missing: [feedback form](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/issues/new?template=feedback.yml). Grok picked the wrong skill? [Report a routing miss](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/issues/new?template=routing-miss.yml). Want a new skill or plugin? [Propose it](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build/issues/new?template=plugin-proposal.yml). Ways to contribute: [CONTRIBUTING.md](./CONTRIBUTING.md).

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreMobileDev-Grok-Build](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
