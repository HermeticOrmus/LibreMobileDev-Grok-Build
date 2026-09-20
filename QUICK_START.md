# Quick Start — LibreMobileDev for Grok Build

> From a clean machine to one mobile review cue in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- `git`
- Grok Build installed and able to see skills under `.grok/skills/` or `~/.grok/skills/`
- A mobile app repo you own (Flutter / RN / native), **or** this repo as the working tree

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```
skills/<name>/SKILL.md                 # canonical skill bodies (copy these)
AGENTS/mobile-orchestrator.md
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok/skills/<name>/SKILL.md           # dogfood copy; must match skills/
.grok/plugins/libremobiledev-core/     # plugin stub; not required for first run
```

Melted (usable now): `skills/mobile-a11y/SKILL.md`, `skills/app-store-checklist/SKILL.md`, `skills/offline-first/SKILL.md`.
Still stubs: the other five skills + the orchestrator. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Dogfood this repo (fastest)

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git
cd LibreMobileDev-Grok-Build
# Skills are already at .grok/skills/ — open this folder in Grok Build.
```

### B. Install into your mobile project

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git ~/LibreMobileDev-Grok-Build
cd /path/to/your-mobile-project
mkdir -p .grok/skills
cp -R ~/LibreMobileDev-Grok-Build/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/mobile-a11y/SKILL.md
test -f .grok/skills/app-store-checklist/SKILL.md
test -f .grok/skills/offline-first/SKILL.md
ls .grok/skills
```

You should see eight skill directories, matching `skills/` in this repo.

### C. User-global

```bash
git clone https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build.git ~/LibreMobileDev-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreMobileDev-Grok-Build/skills/* ~/.grok/skills/
```

Same three `test -f` checks as B, under `~/.grok/skills/`.

Copy `AGENTS/mobile-orchestrator.md` only when you want a multi-pillar pass. It is still a stub coordinator.

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

- [ ] The three melted skill files exist at the install path you chose
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
