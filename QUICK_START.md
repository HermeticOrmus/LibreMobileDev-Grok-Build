# Quick Start — LibreMobileDev for Grok Build

> From a clean machine to one mobile review cue in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- Grok Build installed: `curl -fsSL https://x.ai/cli/install.sh | bash`, then `grok --version`. Plugin commands need no login.
- `git` (only for the dogfood and copy paths); `jq` for the install-everything loop
- A mobile app repo you own (Flutter / RN / native), **or** this repo as the working tree

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```
.grok-plugin/marketplace.json                        # the marketplace: libre-mobiledev-grok, then the pack's plugins by pinned commit
plugins/libre-mobiledev-grok/.grok-plugin/plugin.json
plugins/libre-mobiledev-grok/skills/<name>/SKILL.md  # the melted skills (canonical)
stubs/skills/<name>/SKILL.md                         # stub cues; not installed
stubs/agents/mobile-orchestrator.md                  # stub coordinator; not installed
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok/skills/<name>/SKILL.md                         # dogfood copy; must match its source above
.grok/plugins/libremobiledev-core/                   # v0 bundle stub; dogfood copy of the stub orchestrator
```

Melted (usable now): `plugins/libre-mobiledev-grok/skills/mobile-a11y/SKILL.md`, `plugins/libre-mobiledev-grok/skills/app-store-checklist/SKILL.md`, `plugins/libre-mobiledev-grok/skills/offline-first/SKILL.md`.
Still stubs, in `stubs/`: `flutter-patterns`, `react-native-patterns`, `mobile-perf`, `push-notifications`, `deep-linking`, plus the orchestrator. Each stub names the pack plugin with the real depth. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Marketplace (recommended)

One marketplace brings the Grok-native plugin and every LibreMobileDev-Claude-Code plugin, each pinned to a commit:

```bash
grok plugin marketplace add HermeticOrmus/LibreMobileDev-Grok-Build
grok plugin install libre-mobiledev-grok@LibreMobileDev-Grok-Build
grok plugin install flutter-development@LibreMobileDev-Grok-Build
```

Grok registers a marketplace added from GitHub under the repo's name, so the part after `@` is `LibreMobileDev-Grok-Build`, not the manifest name `libre-mobiledev-grok`. A bare plugin name also works when no other marketplace you added has a plugin by that name.

Every entry at once (needs `jq`):

```bash
for p in $(curl -fsSL https://raw.githubusercontent.com/HermeticOrmus/LibreMobileDev-Grok-Build/main/.grok-plugin/marketplace.json | jq -r '.plugins[].name'); do
  grok plugin install "$p@LibreMobileDev-Grok-Build"
done
```

Confirm what landed:

```bash
grok plugin list
grok plugin details libre-mobiledev-grok
```

You should see `libre-mobiledev-grok` (three skills: `mobile-a11y`, `app-store-checklist`, `offline-first`) plus the pack plugins you installed. The optional `libre-mobiledev-hooks` plugin installs its hooks, but whether they fire inside a Grok session is unverified ([LEDGER.md](./LEDGER.md)).

Only the Grok-native plugin, without the marketplace:

```bash
grok plugin install HermeticOrmus/LibreMobileDev-Grok-Build#plugins/libre-mobiledev-grok
```

Do not install the repo root itself (`grok plugin install HermeticOrmus/LibreMobileDev-Grok-Build`): since v1.0.0 the root holds no skills, so Grok installs an empty plugin.

### B. Dogfood this repo

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git
cd LibreMobileDev-Grok-Build
# Dogfood copies of the melted skills and the stubs are at .grok/skills/; open this folder in Grok Build.
```

### C. Install into your mobile project (copy, no plugin manager)

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git ~/LibreMobileDev-Grok-Build
cd /path/to/your-mobile-project
mkdir -p .grok/skills
cp -R ~/LibreMobileDev-Grok-Build/plugins/libre-mobiledev-grok/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/mobile-a11y/SKILL.md
test -f .grok/skills/app-store-checklist/SKILL.md
test -f .grok/skills/offline-first/SKILL.md
ls .grok/skills
```

You should see three skill directories, matching `plugins/libre-mobiledev-grok/skills/` in this repo. The stubs are not copied: they are cues, not skills.

### D. User-global copy

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git ~/LibreMobileDev-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreMobileDev-Grok-Build/plugins/libre-mobiledev-grok/skills/* ~/.grok/skills/
```

Same three `test -f` checks as C, under `~/.grok/skills/`.

Copy `stubs/agents/mobile-orchestrator.md` only when you want a multi-pillar pass. It is still a stub coordinator, and no install path ships it.

## First-run teach cue

In Grok Build, on a real screen or sync path you own:

1. **A11y** — "Run mobile-a11y on this screen. Name the user job first. Check labels, 44/48 targets, contrast (measure or mark unverified)."
2. **Offline** — "Run offline-first on the primary write. Local source of truth, outbox, named conflict policy."
3. **Store** — "Run app-store-checklist as if we were submitting this RC. No secrets in review notes. Leftover perf/push items stay on the stub skills."

You used melted LibreMobileDev depth on Grok — not a Claude paste, not a fake agent count.

## Hard rules

- Never embed secrets in prompts, examples, or review notes.
- Honest depth — melted vs stub in [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).
- Gold Hat: empower or extract? Teach the rule while you fix.

## Smoke checklist

- [ ] `grok plugin list` shows `libre-mobiledev-grok` (or the three skill files exist at the copy path you chose)
- [ ] Grok can see `mobile-a11y`, `app-store-checklist`, and `offline-first`
- [ ] One a11y pass returned severity-ranked findings (no `/10` score)
- [ ] One store-gate or offline pass named a concrete next action
- [ ] No secrets in output

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreMobileDev-Grok-Build](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof (upstream, not this inventory): [LibreMobileDev-Claude-Code](https://github.com/HermeticOrmus/LibreMobileDev-Claude-Code)
- https://ormus.solutions
