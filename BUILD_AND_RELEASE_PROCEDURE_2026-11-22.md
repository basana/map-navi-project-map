# MAP NAVI — Build, assets and release procedure

**Date:** 2026-11-22  
**Category:** Release / operating procedure  
**Status:** ACTIVE WORKING RULE — requested by project owner; repository architecture still requires a separate verified audit  
**Scope:** Asset paths, build completeness, Preview validation, controlled integration and production release  
**Authority:** This document records the agreed working procedure. It does not identify a final canonical application repository until the current repositories and deployment configuration have been audited.

## 1. Non-negotiable safety boundary

- All development and experiments take place in Preview or isolated development/integration branches.
- Never edit the live application or its production `main` as part of routine development.
- Never merge, publish to production, or trigger a Netlify production deploy without the project owner's explicit, separate approval.
- Project Map is the shared journal and handoff point. Record decisions, branch names, commit SHAs, checks, blockers and release state here.
- Keep four states distinct: **transferred**, **Preview-tested**, **user-approved**, **published**. A commit or successful build is not proof of the later states.

## 2. Source of truth and repository roles

Before choosing a release source, audit the actual repositories, branches, workflows, deployment settings and asset locations. Do not assume that similarly named repositories contain interchangeable or complete copies.

The intended architecture, once verified, is:

1. **Canonical application source:** one clearly identified repository containing the integrated application and all files required to build it.
2. **Development / integration branches:** isolated work areas for Claude, ChatGPT and other contributors. Contributors must not edit the same file concurrently without coordination.
3. **Preview deployment:** a separate deployment target that builds a specific, recorded source commit. Preview is a test destination, not an independent source of truth and not a place for manual one-off fixes.
4. **Production:** built only from the approved release commit in the canonical application repository.

If multiple source repositories genuinely contain separate components, document their boundaries and exact dependency/version relationship. Do not manually mix folders or copy arbitrary files from several repositories at release time.

## 3. Image, icon, font, audio and other asset rules

### 3.1 Keep assets with the application source

Every resource used by the application must be committed to the canonical source repository or be supplied by a documented, versioned external dependency. HTML/JS/CSS without its referenced images, icons, fonts, audio, map data or other runtime files is an incomplete change.

Use a consistent asset directory where practical, for example:

```text
project/
  index.html
  assets/
    images/
    icons/
    fonts/
    audio/
  data/
  maps/
```

This is a proposed organization, not a claim that the current application already has this structure. Adopt it only after auditing the existing code and avoiding unnecessary mass moves.

### 3.2 Use deployment-safe URLs

- Do not hard-code a Preview domain or production domain into ordinary local asset references.
- Prefer paths resolved from a documented application/base path, such as `assets/images/example.webp`, when that matches the actual hosting layout.
- A leading slash (for example `/assets/example.webp`) points to the host root and can break when the app is hosted below a repository or subdirectory path.
- Relative paths such as `./assets/example.webp` are valid only when their resolution from the current document/base URL is correct.
- If the app intentionally uses a `<base href>`, account for it explicitly: relative URLs resolve against that base, not necessarily against the HTML file's folder.
- External URLs are allowed only when intentional, stable, documented and checked. Do not silently rely on a file that exists only in another Preview repository.
- Preserve exact filename case and URL-encode spaces/special characters correctly. Remember that `Image.webp` and `image.webp` are different paths on typical hosting systems.

### 3.3 Asset inventory

For each release candidate, generate or review an inventory of:
- all files included in the build;
- all local resource references found in HTML, CSS, JavaScript and structured data;
- references that resolve to missing files;
- duplicate, orphaned or unexpectedly excluded assets where practical;
- intentionally external resources and their source.

Do not mark an asset as present merely because it exists in a different branch or repository. Verify it in the exact commit and build artifact being tested.

## 4. Mandatory automated checks

GitHub Actions (or the verified CI system) should run on every candidate pull request and again for the exact release candidate. The checks should fail the build for:

1. Missing local files referenced by HTML, CSS, JavaScript or application data, where statically detectable.
2. Broken path resolution under the actual Preview base path, including nested routes/subdirectories.
3. Filename case mismatches and missing expected assets.
4. References accidentally pointing to a different Preview, a developer machine, or an unintended production host.
5. Build, syntax, lint or test failures required by the project.
6. Missing required release files in the final build artifact.

Where static scanning cannot understand dynamically assembled URLs, maintain an explicit asset manifest or test those paths in a browser. A successful static scan does not prove that every runtime-generated resource loads.

After deployment to Preview, run browser/network checks against the deployed page to detect failed image, font, script, stylesheet, audio and data requests (for example HTTP 404/403). Save the run URL, tested commit SHA and result.

## 5. Preview and visual verification

Preview must be built from the exact candidate commit intended for release, including its complete asset set. Record:
- source repository and branch;
- full source commit SHA;
- Preview deployment repository/workflow and run URL;
- published Preview URL;
- build/check result and date.

Then manually inspect the actual Preview, at minimum:
- initial screen and all navigation destinations;
- maps, markers, popups and bottom carousel;
- every changed image and icon;
- key photos, Storymarks and other media;
- mobile portrait (iPhone) and tablet landscape (iPad), where applicable;
- browser console and network failures.

Automated checks and manual device inspection are separate evidence. If a device was not tested, say **not tested**; do not infer success from a desktop build.

## 6. Controlled integration and asset transfer

1. Identify the approved base commit in the canonical application repository.
2. Review each candidate branch and pull request separately. Inspect the diff and dependencies before integration.
3. Integrate only selected, understood changes into one integration/release-candidate branch.
4. Include all required binary assets and data files in the same integration, not just the code that references them.
5. Resolve conflicts deliberately. Do not overwrite a newer image, map dataset or user-approved content merely to make a merge pass.
6. Re-run the asset inventory, path checks, build and tests after integration.
7. Deploy that exact integration commit to Preview and test it. If any file or code changes after testing, the candidate has changed and relevant checks must be repeated.
8. Create a release record containing the exact commit SHA and complete list of included changes/assets.

Do not merge entire repositories into each other simply because changes are spread across them. Use reviewed pull requests, selected commits or a documented integration process. The final application must have one reproducible source tree.

## 7. Release gate — no automatic production publication

Production release is permitted only when all of the following are true:

- repository roles and source commit are identified;
- all intended code and assets are included;
- automated asset/path/build checks pass;
- Preview is deployed from the exact release-candidate SHA;
- required manual browser and device tests are completed and recorded;
- known defects and exclusions are documented;
- rollback point (previous deployed commit/release) is recorded;
- the project owner has explicitly approved this exact candidate for production.

Only then may the approved candidate be merged/promoted and production deployment be initiated according to the verified hosting workflow. Record the production deployment URL, deployed commit SHA, workflow result and post-deploy smoke test.

**No approval means no production merge and no production deploy.** A successful Preview is not itself permission to publish.

## 8. Responsibilities

| Participant | Responsibility |
|---|---|
| Claude / other contributor | Make scoped changes on the assigned isolated branch; report files, branch and commit; do not publish production |
| ChatGPT | Maintain Project Map, inspect diffs and repository evidence, review asset/path reports, distinguish verified facts from assumptions, report blockers and release readiness |
| CI / GitHub Actions | Repeatable static checks, asset existence/path checks, build and automated tests; publish Preview only to its designated target |
| Project owner | Review Preview, decide whether the candidate is acceptable, and explicitly authorize or refuse production release |

No assistant should claim that visual testing, deployment or a merge happened unless the relevant result is actually available and verified.

## 9. Release checklist

- [ ] Canonical application repository and release branch verified
- [ ] Candidate source commit SHA recorded
- [ ] All required images/icons/fonts/audio/data included in that commit
- [ ] Asset inventory generated/reviewed
- [ ] No missing local asset references
- [ ] Base-path and Preview URL checks passed
- [ ] Build, syntax and required automated tests passed
- [ ] Preview built from the exact candidate SHA
- [ ] Browser network/console check completed
- [ ] iPhone portrait test completed, if applicable
- [ ] iPad landscape test completed, if applicable
- [ ] Changed screens and media visually checked
- [ ] Known issues and skipped tests documented
- [ ] Rollback commit identified
- [ ] Project owner explicitly approved this exact candidate
- [ ] Production merge/deploy completed only after approval
- [ ] Production URL, deployed SHA and smoke-test result recorded

## 10. Current status / next prerequisite

This procedure is saved as the working release rule. It does **not** mean that automated checks have already been implemented or that the present repositories have been consolidated.

Next technical prerequisite: perform a read-only audit of the current application repositories, branches, workflows, base URLs, asset trees and hosting configuration. From that evidence, identify the canonical source and the smallest safe changes needed to enforce this procedure. Until then, do not merge repositories, reorganize asset folders, alter application `main`, or change production deployment settings.
