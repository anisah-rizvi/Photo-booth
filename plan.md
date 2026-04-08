

## Vintage Photobooth — Build Plan

### Design Reference (from uploaded screenshots)

The app is a Valentine's-themed vintage photobooth with a purple/lavender color palette. The flow:

1. **Intro** — "be my valentine's?" heading, name "gena,", a "start" button, curtain illustration on the right, boot illustration swinging at bottom-right, checkered pattern at bottom
2. **Black screen** — transition screen (solid black)
3. **Countdown** — 3, 2, 1 countdown with large italic serif numbers on a muted purple/grey background
4. **Capture** — webcam captures 3 photos (repeats countdown 3 times)
5. **Printing** — "photo is printing" with a Polaroid-style frame on purple background, checkered pattern at bottom
6. **Reveal 1** — tilted vintage photo strip with 3 photos, kewpie cupid overlay, "Marisa & Gena / Valentine's 2026" text, on lavender background
7. **Reveal 2** — photo strip + a handwritten-style note card ("Gena, I wish you peace, happiness, and less back pain — Marisa")

### What to Build

**Files to create:**
- `src/pages/Index.tsx` — main state machine orchestrating all screens
- `src/components/IntroScreen.tsx` — welcome screen with curtain, animated swinging boot, start button
- `src/components/CountdownScreen.tsx` — 3-2-1 countdown with serif italic numbers
- `src/components/CaptureScreen.tsx` — webcam feed + countdown, captures 3 photos
- `src/components/PrintingScreen.tsx` — "photo is printing" animation with Polaroid frame
- `src/components/RevealScreen.tsx` — tilted photo strip with captured photos, note card overlay
- `src/components/BlackScreen.tsx` — simple black transition screen

**Key technical details:**
- Webcam via `navigator.mediaDevices.getUserMedia()`, capture to canvas
- State machine: `intro → black → capture(×3 with countdowns) → printing → reveal`
- **Swinging boot animation**: CSS keyframe animation using `transform-origin` at top, rotating back and forth (pendulum swing)
- Photo strip: 3 captured images arranged vertically in a vintage paper-textured strip, tilted ~15deg
- Color palette: primary purple `#7C3AED`, background lavender `#C4B5FD` / `#DDD6FE`, accents in pink/peach
- Typography: serif italic for countdown numbers and headings, cursive/script for the note card
- Checkered pattern at bottom via CSS gradient or SVG
- Download button on reveal screen to save the photo strip as an image (html2canvas)

**Boot animation (user's specific request):**
- The boot in the intro screen will have a pendulum-swing CSS animation
- `transform-origin: top center` with `@keyframes swing` rotating between -15deg and 15deg
- Continuous, gentle swinging motion

**Assets needed:**
- Curtain and boot will be drawn as SVG inline or simple CSS illustrations matching the purple line-art style from the Figma
- Kewpie cupid overlay for the photo strip (SVG or inline illustration)

### Flow Diagram

```text
[Intro] --tap start--> [Black 1s] --> [Countdown 3-2-1] --> [Capture Photo 1]
  --> [Countdown 3-2-1] --> [Capture Photo 2]
  --> [Countdown 3-2-1] --> [Capture Photo 3]
  --> [Printing 3s] --> [Reveal Strip + Note]
```

