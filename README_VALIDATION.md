# AJMATICS GitHub README — validation notes

## What is included

- A custom, locally hosted neon AJMATICS hero banner (`images/ajmatics-banner.svg`).
- A custom engineering-flow illustration and section divider (`engineering-flow.svg`, `ajmatics-divider.svg`).
- The original butterfly, dog and footer assets are retained.
- The developer-at-work GIF from SP-XD is retained using its direct `raw.githubusercontent.com` image path.
- The original typing effect, GitHub streak card and contribution-snake concept are retained. GitHub stats, top languages and activity charts are now generated as SVG assets by GitHub Actions and served from this repository.
- The original experience, internship, early-career, project, interest, technical-writing, credentials, education and connect sections are restored or expanded.
- `.github/workflows/snake.yml` generates contribution-snake SVGs for this repository and publishes them to its own `output` branch.
- `.github/workflows/profile-stats.yml` generates `profile/stats.svg` and `profile/top-langs.svg` using the maintained GitHub Stats Extended Action.
- `.github/workflows/activity-chart.yml` generates 30-, 90- and 365-day activity SVGs using the Deus Commit Chart Action and commits them to `profile/`.

## Local checks completed

- All local image references in `README.md` resolve inside the repository package.
- All SVG assets parse as valid XML.
- The README was parsed using a CommonMark renderer with HTML and table support.
- The contribution-snake workflow YAML parses as a mapping. GitHub Actions execution itself can only be verified after the workflow is pushed to GitHub.
- The project bank includes all 12 projects captured in the career master profile, along with the early Diploma-Connect, SwapraTech and student-performance work.
- The broader technology and capability inventory is grouped into badges and compact keyword clusters. It is deliberately not reduced to a tiny role-specific skills list.

## External visual services and image checks

| Asset / service | Treatment | Verification note |
|---|---|---|
| `imgur.com/rilHVxA.png` | Removed; replaced by local `engineering-flow.svg` | The supplied URL redirected to an Imgur HTML page instead of behaving as a direct image URL. |
| SP-XD developer GIF | Retained with a direct `raw.githubusercontent.com` image URL | The browser checker recognised the GIF media type but does not preview binary GIF content. This is not enough to certify the final GitHub-rendered image; verify visually after publishing. |
| Typing SVG | Updated to `readme-typing-svg.demolab.com` | The current upstream project documentation uses the `.demolab.com` host. |
| GitHub streak | Updated to `streak-stats.demolab.com` | The current streak-stats demo documents this host. |
| Activity graph | Replaced with GitHub Actions-generated static SVGs in `profile/activity-*.svg` | The old `github-readme-activity-graph.vercel.app` public deployment is reported disabled; the new chart does not call an external service when the README is viewed. |
| GitHub stats cards | Replaced with locally stored `profile/stats.svg` and `profile/top-langs.svg` | Generated daily by the maintained `stats-organization/github-readme-stats-action`; no third-party API is called at profile-view time. |
| Contribution snake | Replaced the old `platane/platane` output URL with this account's own workflow output | It will display only after the workflow is pushed and completes successfully at least once. |
| Shields.io badges | Retained and expanded | Badge URLs are standard Shields endpoints; every individual badge endpoint was not independently fetched in this environment. |

## Public profile and link checks

| Profile / resource | Check result | README treatment |
|---|---|---|
| GitHub `atharvajoshi1007` | Public profile resolves | Linked. |
| CodeChef `ajmatics` | Profile resolves with the expected username | Linked. |
| LeetCode `ajmatics` | Profile resolves and displays Atharva Joshi | Linked. |
| Medium `@atharvajoshi1007` | Public profile resolves and displays technical articles | Linked, with selected published articles featured. |
| Linktree `atharva.joshi` | Public page resolves and lists the personal website, LinkedIn, GitHub, Medium and social links | Linked. |
| Personal website `atharva-joshi.vercel.app` | Linked from the verified Linktree; page returned no readable text to the browser parser | Linked as supplied through Linktree; visual/content review remains a separate task. |
| Instagram | Linktree currently points to `instagram.com/_atharvajoshi_` | Updated to that handle; the older `instagram.com/atharvajoshi1007` value was not used. |
| X / Twitter | Linktree points to `x.com/atharvajoshi107`; X blocks automated page inspection | Linked using the Linktree destination. |
| LinkedIn `atharvajoshi10` | Automated fetch returned an access/status error, not a reliable indication of a broken profile | Retained; recheck in a normal browser. |
| HackerRank `atharvajoshi1001` | Supplied profile URL returned a 404 page | Omitted from the active click-through row until the correct profile URL is available. |
| Cwipedia `Diploma-connect` repository | Original repository URL returned 404 | Project is retained, but the old repository URL is not presented as a working source link. |
| SwapraTech project path | The public repository root resolves. The folder-level link was restricted by the browser checker, so the README links to the confirmed repository root. |

## Notes before publishing

1. Push the README, `images/` assets and `.github/workflows/snake.yml` together. Do not upload only the README; the local SVG and animation references need the assets folder.
2. After the first push, open **Actions → Generate contribution snake**, confirm it succeeds, and check that the `output` branch contains both SVG files. The snake will not appear before that first successful run.
3. Open the live GitHub profile on desktop and mobile. Check the remote developer GIF, typing SVG, streak card, locally generated stats and activity chart. Third-party dynamic cards can be intermittently unavailable even when their Markdown is correct.
4. Refresh the HackerRank profile URL before adding that icon back. Restore the Diploma-Connect source link only after locating the current repository URL.
5. Run **Actions → Update GitHub profile cards → Run workflow** and **Actions → Update GitHub activity chart → Run workflow** once after the first push. Both workflows also run daily. The first run creates the local SVG files referenced by the README. The streak card remains a third-party live image, because it is currently the only live card that was working in the supplied block.
6. No audio player was added. GitHub profile Markdown is a poor place for an autoplay/audio widget, and no relevant original audio asset was supplied. A genuine talk/demo recording can be linked later if available.

## Scope limitation

This package has been checked locally for structure, relative assets and SVG validity, and selected public links/services were checked through the available browser. The browser environment cannot render every remote GIF/SVG/API response, and the exact GitHub production renderer cannot be reproduced here. Treat the first GitHub deployment as the final visual smoke test, not as a guarantee that every third-party service will stay online.


## GitHub playground repair (31 October 2026)

The supplied block used two services that are not dependable at present:

- `github-readme-stats.vercel.app` belongs to the original `github-readme-stats` project, whose repository now states that it is no longer maintained and points users to GitHub Stats Extended or its GitHub Action.
- `github-readme-activity-graph.vercel.app` is reported disabled / paused in October 2026.

The README now uses repository-hosted SVGs for stats, languages and activity. Two workflows create them: `.github/workflows/profile-stats.yml` and `.github/workflows/activity-chart.yml`. The existing streak card is retained at `streak-stats.demolab.com`, since it is the only supplied visual confirmed by the user as loading. The snake workflow remains separate.

### First deployment steps

1. Push the complete package to `atharvajoshi1007/atharvajoshi1007` on the `main` branch.
2. In **Settings → Actions → General → Workflow permissions**, ensure Actions can write to the repository (or confirm the workflow-level `contents: write` permission is permitted by repository policy).
3. Open **Actions → Update GitHub profile cards → Run workflow**.
4. Open **Actions → Update GitHub activity chart → Run workflow**.
5. Confirm the generated files appear under `profile/`, then refresh the profile. The first run is required because those files are generated artifacts and are not included as fake placeholders in this package.

The public contribution calendar is used; no personal access token is required for ordinary public contribution activity. A successful local YAML parse does not guarantee that GitHub Actions will execute successfully; the first actual run is the deployment test.
