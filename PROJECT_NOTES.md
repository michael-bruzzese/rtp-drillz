# RTP Drillz - Project Notes

## Purpose
Stable core web drill for range-based postflop decisions (no recorder UI).

## Live App
- https://michael-bruzzese.github.io/rtp-drillz/

## Current Feature Snapshot
- Random playable preflop hand generator.
- Street drill flow: hand -> flop -> turn -> river -> done.
- Street rerolls (`New Hand`, `New Flop`, `New Turn`, `New River`).
- `Go Back a Street` action:
  - done -> river
  - river -> turn (keeps flop+turn)
  - turn -> flop (keeps flop)
  - flop -> hand
  - hand -> start
- `Start Over` always available (non-start states).
- Timer per street with selectable durations, pause/resume button, last-5-second tick sounds, `TIME!` overlay + flash.
- Spot configuration selectors on table:
  - Left: `SRP/3BP/4BP`, `IP/OOP`, `PFR/PFC` (single-select per row)
  - Right: `Effective Stacks` single-select (`50BB` to `500BB+`)
- Under-board status line now shows only left-side tags (`SRP | IP | PFR` style).
- Tag selections persist until user changes them; `Start Over` clears all.

## Key Files
- `rtp_drillz_web.html` (source web UI/logic)
- `rtp_drillz_web_embedded.html` (deployed embedded cards build)
- `build_embedded_rtp_drillz.py` (embeds card PNG data URIs)
- `index.html` (redirect to embedded file for GitHub Pages)

## Rebuild + Deploy
```bash
python3 build_embedded_rtp_drillz.py \
  --cards-dir /Users/michaelj.bruzzese/Downloads/PNG-cards-1.3 \
  --template ./rtp_drillz_web.html \
  --output ./rtp_drillz_web_embedded.html
git add rtp_drillz_web.html rtp_drillz_web_embedded.html
git commit -m "Describe change"
git push
```

## Next Session Quick Start
1. Read this file and `CHANGELOG.md`.
2. Open the live app and verify expected behavior.
3. Edit `rtp_drillz_web.html`, rebuild embedded output, commit/push.
