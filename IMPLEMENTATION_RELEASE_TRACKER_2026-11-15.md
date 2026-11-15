# MAP NAVI — Implementation & Release Tracker
**Last updated:** 15 November 2026, Europe/Berlin  
**Purpose:** one checklist for transferring already-developed navigation improvements into the existing Netlify application before the first guided tour on 27 November 2026.

## Release target

- **25 November 2026:** latest planned date for the user's Netlify deployment.
- **26 November 2026:** verify the actual published Netlify site, not only a GitHub Preview.
- **27 November 2026:** first guided tour; a stable conventional map/navigation version must be usable even if the 3-level spatial layer is not ready.

The dates are a working plan, not a claim that any transfer, test, or deployment has already happened.

## Working agreement

1. Keep the existing application and its existing Netlify publishing workflow.
2. Make changes in a separate branch of `basana/turret-tales-christmas`.
3. Do not change or merge into `main`, and do not publish to Netlify, without the user's explicit approval.
4. Compare each change with the current source before transferring it. A feature seen in Preview is not automatically present in the production repository.
5. Keep commits small and identifiable; record branch, commit SHA, test result, and remaining issues here.
6. The user reviews the Preview / branch and makes the final Deploy.
7. The spatial 3-level architecture and Storymarks remain a separate workstream; they must not block the stable navigation release.

## Existing work and evidence

### Application repository
- Repository: [basana/turret-tales-christmas](https://github.com/basana/turret-tales-christmas)
- Existing GPS work branch: [feature/map-navi-gps-follow-01](https://github.com/basana/turret-tales-christmas/tree/feature/map-navi-gps-follow-01)
- Preview branch: [preview/gps-follow-device-test-01](https://github.com/basana/turret-tales-christmas/tree/preview/gps-follow-device-test-01)
- Draft PR #2: [GPS Follow device test](https://github.com/basana/turret-tales-christmas/pull/2)
- Known GPS branch commits: `666507c` (GPS Follow / Free View), `02a2a82` (manual recenter fix), `56e011e` (right-side POI/reset controls).
- Known scope: `index.html` in the GPS branch. Syntax checks were reported for four inline JavaScript blocks; that is not the same as full browser/device verification.
- The Preview repository `basana/turret-tales-preview` is a test shell and uses a `<base href="https://turrettales.de/">`; some assets/content may still come from the live site. Do not treat its changes as already transferred into the application repository.

### Preview-only improvements to compare and transfer if confirmed
- POI auto-focus: selecting Pharmacy / Toilets should automatically focus the nearest relevant POI, with the same pan/zoom behavior as tapping its marker; active POI focus should not be overridden by GPS Follow.
- Search and ticker layout adjustments.
- Mobile width/layout refinements.
- Toast positioning and search overlay stacking.
- Market-map zoom-control vertical positioning.
- Any additional visual or control fixes found in the current Preview.

The above list is an inventory to verify against the actual repository and current Preview source. It does not certify that every item is complete or ready to merge.

## Transfer checklist

### A. Audit and prepare — 15 November
- [ ] Read current default branch and working branches in `basana/turret-tales-christmas`.
- [ ] Identify the exact Netlify-connected branch / publishing configuration; do not assume it is `main` without checking.
- [ ] Compare the GPS branch, Preview branch, and Preview shell; list every relevant file and commit.
- [ ] Identify dependencies and conflicts, especially `index.html`, `sw.js`, manifests and map-specific scripts.
- [ ] Create or select one clean integration branch from the correct current base. Do not overwrite existing work.

### B. Transfer ready improvements — target 15 November, continue as needed
- [ ] GPS Follow / Free View.
- [ ] Manual recenter and `↻ Follow` behavior.
- [ ] Consistent right-side Pharmacy / Toilets / Reset controls.
- [ ] POI auto-focus and camera-priority behavior.
- [ ] Search / ticker / overlay layout.
- [ ] Toast positioning and map zoom-control adjustments.
- [ ] Record each transferred change with its commit SHA and source.

### C. Functional and device verification — 16–22 November
- [ ] Main Koblenz / castle map: GPS on, Follow, manual pan/zoom, Free View, return to Follow.
- [ ] Pharmacy search: nearest result, focus, distance/label, route action if available.
- [ ] Toilets search: nearest result, focus, distance/label; no unrelated castle focus.
- [ ] Confirm active POI focus is not pulled away by GPS updates.
- [ ] Check reset-to-full-map behavior.
- [ ] Check search, legend, buttons, toast and zoom controls on iPhone portrait and iPad landscape.
- [ ] Check all relevant map pages, including markets; do not assume a fix on one map has propagated to others.
- [ ] Check browser console / JavaScript errors and basic navigation after reload.
- [ ] Record what was actually tested and what remains unverified.

### D. Freeze and release — 23–26 November
- [ ] 23–24 Nov: freeze the candidate; no risky new features.
- [ ] 25 Nov: user reviews and performs Deploy to Netlify from the agreed GitHub source.
- [ ] 26 Nov: test the live Netlify URL on the actual device and confirm the deployed commit/version.
- [ ] Keep a rollback point and record the deployed commit SHA.
- [ ] If a blocking issue remains, revert only the problematic change or deploy the last known-good version.

## Release rule

A change is not considered complete merely because it exists in a branch or passes syntax checks. Track these separately:
- **Transferred:** present in the integration branch.
- **Preview-tested:** exercised in the browser / device Preview.
- **User-approved:** user has accepted the behavior.
- **Deployed:** present on the live Netlify site after the user's Deploy.

## Out of scope for the 27 November safety release

The 3-level isometric architecture, full spatial relationships, and Architectural Storymarks may continue in parallel. They are not prerequisites for a dependable conventional map, GPS and POI navigation.

## Change log

### 15 November 2026
- User confirmed that all transfer work and release tracking must be recorded in the MAP NAVI Project Map.
- Agreed to preserve the existing GitHub → Preview/review → user-controlled Netlify Deploy workflow.
- Agreed not to modify production `main` or publish without explicit user approval.
- Set the first-tour safety target: stable release ready for user deployment by 25 November; live-site verification on 26 November; first tour on 27 November.
- No application code was changed by this tracker entry. Transfer and verification remain pending.
