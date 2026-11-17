# MAP NAVI — Reset and Popup Manager integration record

**Date:** 2026-11-17  
**Category:** IMPLEMENTATION  
**Status:** Implemented on an isolated branch; awaiting runtime verification  
**Repository:** `basana/turret-tales-christmas`  
**Branch:** `feature/map-navi-stabilized-integration-2026-11-17`  
**Commit:** `39836e1c83920bdb78fefac2810fde8b0daa0d05`  
**Base branch:** `feature/map-navi-integration-2026-11-15`  
**Base commit:** `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`  
**Draft PR:** https://github.com/basana/turret-tales-christmas/pull/6

## Implemented

- Ported Reset cleanup onto the map integration line.
- Reset removes pharmacy/toilet layers, clears active controls and pending POI focus, hides POI/GPS hints, stops POI emergency mode, closes the selected-object panel, clears selection, restores full-map bounds, and pauses GPS camera-follow while leaving GPS position updates active.
- Reset suppresses an immediate duplicate nearest-castle toast while retaining future notifications when the nearest castle changes.
- Ported Popup Manager context gating onto the same integration line.
- Automatic offers are suppressed during urgent POI tasks, text entry, open object-detail reading, other modals, and active routes.
- Food & Drinks, Souvenirs, Guided Tours and POI prompt timers no longer show their former timer-driven invitations.
- Guided Tours is offered contextually on entry to Christmas, Wine, Castles and Route sections, at most once per section per page session; active urgent contexts block it.
- Existing integration-branch delayed POI focus and GPS distance-panel behavior are retained.
- Existing user-provided vintage visual assets were not replaced.

## Integration method

The two feature branches had diverged from a shared base. A three-way line merge was performed using that common base. The Reset source was reconstructed byte-for-byte from the base plus its 25 change hunks; the Popup Manager source was reconstructed byte-for-byte from the base plus its 29 change hunks. No overlapping edit ranges were found. The combined result was then compared against the integration branch.

## Scope and change summary

Compared with `feature/map-navi-integration-2026-11-15`: 7 commits ahead, 0 behind; only `index.html` changed (232 additions, 44 deletions at the recorded commit).

## Not changed

- No edits to `main`.
- No merge into production.
- No deployment or Netlify action.
- No paid map provider or server setup.
- No offline map implementation.

## Validation and limitations

Focused Reset harness: 6/6 passed.  
Focused Popup Manager harness: 6/6 passed.  
Guided Tours context harness: passed for all four sections and urgent-context suppression.  
Static script scan: blocks 1–3 and 5–7 passed; block 4 has the same pre-existing parse failure as the integration base.  
No CI status checks were reported at the recorded commit.

Real browser and iPhone runtime testing remains outstanding. This branch is not declared release-ready.
