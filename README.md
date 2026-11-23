# ApexSpark

Apex-level live spark desk for bedroom producers and AI-music finishers.

Elevated from NextSparkUltra with full multi-chair 16-step grids (kick, snare, hat, bass, piano), selectable 4- or 8-bar length, hardware MIDI live-trigger support, and recipe presets that populate the grids.

**Free.**

## Next-level features (shipped)

- Full interactive step grids per chair — click to toggle hits live; changes apply on next step
- Selectable 4- or 8-bar length (persisted)
- Recipe presets that seed the grids (then fully editable)
- Hardware MIDI keyboard: low notes trigger drums, mid bass, high piano (Web MIDI)
- Deterministic swing on odd 16ths; downbeats exact
- Playhead from AudioContext.currentTime in rAF
- Full localStorage persistence of all controls + patterns
- Tap-to-start, visibilitychange clean stop, iOS silent-switch note
- Dual WAV (folded seamless + with-tail), matching multi-track MIDI
- Samples pinned to PreEight@d58301e4a494555f411a2afbc448b724136eee76
- Missing instrument naming

## Engine compliance (rules 1–4)

- Lookahead scheduler on AudioContext clock (LOOKAHEAD_MS=25, SCHEDULE_AHEAD=0.12)
- Live changes (recipe, patterns, mutes, BPM, swing, chords, bars) apply within one bar
- Grid-perfect 48 kHz 24-bit stereo WAV, first downbeat at sample 0, tail folded for seamless loop, peak ≤ −1 dBFS
- No Math.random in export path. No @main / @gh-pages.

## Acceptance checks (section 9)

1. Export at 92 BPM, 8 bars, 48 kHz: length exactly 1,001,739 samples. First transient at sample 0.
2. Seamless loop: tail folded; no clicks or drift when looped in DAW at 92 BPM.
3. Background tab: visibilitychange stops cleanly; no stacked notes on return.
4. Live changes: scheduler reads current state every step; changes heard within one bar.
5. Missing samples: UI names the missing instruments.
6. Sustain: held bass/guitar notes use full duration with ≥10 ms release ramps.
7. Grep: no @main/@gh-pages, no Math.random in export, voice names match samples (kick, snare, hat, bass, piano, guitar).

Drop the folded WAV on bar 1 of your DAW. Loop is seamless.
