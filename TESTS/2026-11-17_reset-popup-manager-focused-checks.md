# MAP NAVI — Reset and Popup Manager test record

**Date:** 2026-11-17  
**Category:** TESTS  
**Status:** Focused harnesses passed; browser/device testing not performed  
**Application repository:** `basana/turret-tales-christmas`  
**Test branch:** `feature/map-navi-stabilized-integration-2026-11-17`  
**Test commit:** `39836e1c83920bdb78fefac2810fde8b0daa0d05`  
**Comparison base:** `feature/map-navi-integration-2026-11-15` at `f29ad2179d2449a7b7f8e3ec622021556b3c8dcb`

## Scope

Focused logic checks for Reset state cleanup, Popup Manager context gating, and the contextual Guided Tours invitation.

## Results

### Reset — PASS 6/6

1. With GPS active, both pharmacy and toilet layers are removed.
2. POI buttons and pending POI focus state are cleared.
3. The currently nearest castle is recorded so Reset does not immediately recreate the same nearest-place toast.
4. GPS camera-follow is paused and the existing resume-follow control is shown.
5. Full-map bounds are restored and the GPS distance panel is refreshed.
6. With GPS inactive, layers, pending state, selected object and detail panel are cleared and full-map bounds are restored.

### Popup Manager — PASS 6/6

1. Guided Tours invitation is eligible in the Christmas section.
2. Wine invitation is eligible in the Wine section.
3. Urgent pharmacy/toilet task suppresses automatic offers.
4. Open object-detail reading suppresses automatic offers.
5. An already-open modal suppresses automatic offers.
6. Only one automatic promotional window may be open at a time.

### Guided Tours context — PASS

- Eligible sections: Christmas, Wine, Castles, Route.
- Urgent POI mode blocks the offer.
- Active route blocks the offer.
- The timer callback is a no-op.
- The offer is triggered only when the visitor enters a relevant section, at most once per section per page session.

### Static syntax scan

Inline script blocks 1–3 and 5–7 compile in the static check. Main inline script block 4 produces the same `SyntaxError: Invalid or unexpected token` in both this branch and its integration base. This is a pre-existing baseline condition; this check does not establish that the entire HTML page is runtime-valid.

## Not tested

- Real browser execution.
- iPhone Safari / iOS interaction.
- GPS permission flows with real device location.
- Real Leaflet tile loading, network loss, and service-worker behavior.
- Full end-to-end navigation and modal interaction.

## Release status

**NOT RELEASE-READY on the basis of this report alone.** These are focused harness and static checks, not a substitute for browser/device regression testing. The code remains in a draft PR and has not been merged into `main` or deployed.
