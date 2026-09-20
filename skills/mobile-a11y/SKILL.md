---
name: mobile-a11y
description: Mobile accessibility for VoiceOver, TalkBack, hit targets, contrast, and dynamic type. Use when auditing or fixing a screen or control in Flutter, React Native, iOS, or Android.
---

# Mobile A11Y

Make one screen or control usable with a screen reader, a finger, and larger type. Platform APIs differ; the job does not.

Gold Hat: name the user who cannot see, hear, or precisely tap the control, then teach the rule while you fix it. A silent icon-only close that "looks clean" extracts. Leaving the next engineer able to judge the next screen empowers.

## When to use

- A new screen, sheet, or custom control
- Icon-only, gesture-only, or color-only UI
- Before store submit (pair with `app-store-checklist`)
- After a visual polish pass that likely dropped labels or shrunk targets

Do not use this as a full product WCAG certificate. Do not invent a `/10` a11y score. Hand leftovers to still-stub skills: `flutter-patterns` / `react-native-patterns` (stack fit), `mobile-perf` (jank from live regions or huge type). Call the stub; do not invent its depth.

## Operating steps

1. **Name the job.** Who is on this screen, what must they accomplish, what is the one primary action?
2. **Walk the tree.** Every interactive node needs a name, a role, and a state/value. Decorative nodes are hidden. Related children are merged.
3. **Measure targets and contrast.** Platform target first (table below). Contrast: measure or mark **unverified**. Do not invent a ratio.
4. **Scale and motion.** Dynamic type must not clip primary copy or overlap actions. Honor reduce-motion.
5. **Smoke on a reader.** VoiceOver or TalkBack on the real screen beats an inspector-only pass. If you did not run a reader, say so.

Stop if you cannot name the primary action. Ask. Guessing labels is extraction.

## Checks (measurable)

### Name, role, value

Screen reader users hear what you expose, not what you painted.

| Check | Pass | Fail |
|-------|------|------|
| Name | Interactive control announces a human name | Icon-only `Image` / `Icon` with no label |
| Role | Button sounds like a button; heading is a heading | Tappable `View` / `div` / `GestureDetector` with no role |
| State / value | Toggle, tab, slider, rating announce current value | Switch that only says "button" |
| Decorative | Logo/texture/Lottie hidden from the tree | Background art in the swipe order |
| Grouping | Card or row reads as one node | Name, price, and chevron as three stops |

Flutter: `Semantics` / `MergeSemantics` / `ExcludeSemantics`. React Native: `accessibilityLabel`, `accessibilityRole`, `accessibilityState`, `accessible`. iOS: `accessibilityLabel` + traits. Android: `contentDescription` / Compose `semantics`.

### Hit targets

Prefer the **platform** bar. WCAG 2.2 AA SC 2.5.8 floor is **24×24 CSS px** — say which bar you used.

| Platform | Minimum | Fail |
|----------|---------|------|
| iOS | 44×44 pt | 28 pt icon, no hit-slop |
| Android | 48×48 dp | 32 dp Material icon button |
| Flutter (Material) | 48×48 dp | Tiny `IconButton` without `minimumSize` / padding |
| React Native | 44×44 (iOS) / 48×48 (Android) | `Pressable` sized to the glyph |

Extend the hit area (padding, `hitSlop`, `TouchDelegate`) when the glyph must stay small. Visual size ≠ target size.

### Contrast

WCAG 2.2 AA:

- Body / normal text: **4.5:1**
- Large text (18pt regular or 14pt bold) and UI chrome vs adjacent color: **3:1**
- Color is never the only status signal

If you did not measure (Xcode Accessibility Inspector, Android Accessibility Scanner, a contrast checker, or a known token pair), write **unverified**.

### Dynamic type and motion

| Check | Pass | Fail |
|-------|------|------|
| Type scale | Primary copy and the primary action still work at the large accessibility size | Fixed-height row clips at 2× text |
| Motion | Honor reduce-motion / `disableAnimations`; motion is feedback, not the only cue | Required swipe with no button equivalent; looping decoration that ignores reduce-motion |
| Focus after change | Modal or new list lands focus on the first meaningful node | Focus left on the dismissed control or the status bar |

## Worked example — icon-only close

Job: dismiss a product sheet. Primary action: Close.

Weak (Flutter):

```dart
GestureDetector(
  onTap: () => Navigator.pop(context),
  child: Icon(Icons.close),
)
```

No name, no button role, target is the 24dp glyph.

Stronger:

```dart
IconButton(
  icon: const Icon(Icons.close),
  tooltip: 'Close',
  style: IconButton.styleFrom(minimumSize: const Size(48, 48)),
  onPressed: () => Navigator.pop(context),
)
```

- **Name / role:** `IconButton` + tooltip → "Close, button".
- **Target:** 48×48. Glyph can stay 24.
- **Decorative:** the icon is the button; do not also announce "close icon".

React Native equivalent: `Pressable` with `accessibilityRole: 'button'`, `accessibilityLabel: 'Close'`, `hitSlop` or min 44/48 height. iOS: `accessibilityLabel = "Close"` + `.button` trait. Android: `contentDescription` + 48dp min.

Three concrete fixes if you only have the weak widget: (1) real button semantics + "Close", (2) 44/48 target, (3) after dismiss, confirm focus returned to the opener — then run `app-store-checklist` before submit.

## Reader smoke (if you have a device)

VoiceOver: Settings → Accessibility → VoiceOver. Swipe through every node. Each control: `[name], [role]`. No traps. After a push/modal, focus is on the new title or first field.

TalkBack: Settings → Accessibility → TalkBack. Same linear pass. Cards read as one unit. Live updates announce once, politely.

No device: dump the semantics tree (`debugDumpSemanticsTree()`, RN accessibility inspector, Xcode/Android inspector) and mark the reader pass **unverified**.

## Output shape

```markdown
## Job
[who / task / primary action]

## Platform + bar
[iOS 44 | Android 48 | Flutter 48 | RN 44/48] — [reader run | unverified]

## Findings
1. **[Critical|High|Medium|Low] — [check].** [element] [current] → [needed]
2. …

## Fixes now
1. …
2. …
3. …

## Teach
[one reusable sentence]

## Leftovers
- [stub skill] — [what you did not pretend to finish]
```

Severity: **Critical** blocks the reader or the tap on the primary action. **High** causes hesitation (two equal names, 28dp submit). **Medium** is grouping or hint debt. **Low** is polish. Empty findings are allowed. Invented issues are not.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
