# CNCF Sandbox Onboarding

Single source of truth for completing [CNCF Sandbox onboarding](https://github.com/cncf/sandbox/issues/487) after your project's TOC acceptance vote.

**Work here only:** each item shows `(Issue: …)` until you open a PR with `Closes #N`; automation then checks the box and shows `(PR: …)` here and in [README.md](README.md). Edit evidence below; do not edit README or toggle boxes yourself.

Onboarding should be completed within **one month** of acceptance. When everything is done (or intentionally N/A), run `./scripts/generate-status-report.sh` to produce an update for your CNCF onboarding issue.

---

## Required before CNCF staff can proceed

A signed Project Contribution Agreement and trademark transfer are required **before** CNCF staff can complete the rest of onboarding. Other items can be worked on in parallel.

### ip-policy-review

<!-- field-guide:start -->
Review the [CNCF IP Policy](https://github.com/cncf/foundation/blob/main/charter.md#11-ip-policy). Ensure the project uses a CNCF-compatible license — inbound projects must use **Apache 2.0**. (Dependency licenses are tracked separately in `license-scan-import`.)
<!-- field-guide:end -->

- [x] Review and understand the CNCF IP Policy <!-- checklist:ip-policy-review --> (PR: [#50](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/50))

**Evidence:**

- Maintainer @clubanderson reviewed and accepts the [CNCF IP Policy](https://github.com/cncf/foundation/blob/main/charter.md#11-ip-policy) on 2026-10-02.
- Compliance check: inbound project code is Apache-2.0. `gh repo list hivecommons --json name,licenseInfo` reported Apache License 2.0 for every current public Hive Commons repo, and each repo's root `LICENSE` was verified as Apache License 2.0:
  - `hive` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `cncf-sandbox-onboarding` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `hivecommons.github.io` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `rationguard` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `hotshot` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `homebrew-hive` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `dibs` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `promptargs` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `docs` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `pluk` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `spektacular` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `.github` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `spektacular-website` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `hive-redirect` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `homebrew-repo` → Apache License 2.0 (`LICENSE` verified on default branch)
  - `infra` → Apache License 2.0 (`LICENSE` verified on default branch)
- Hive documentation under `README.md`, `src/README.md`, and `src/docs/` is covered by the repository Apache-2.0 license. CNCF site documentation referenced for onboarding is CC-BY-4.0 where applicable.
- Inbound contribution control is DCO, verified in `dco-enabled` evidence ([#40](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/40)).
- Third-party dependency license policy is tracked separately in `license-policy-review` (#35); no repository source license conflicting with the IP policy was found in this IP-policy check.
- Trademark/logo transfer is tracked separately in `trademark-transfer` (#33) and remains pending, not a blocker for this evidence item.

### license-policy-review

<!-- field-guide:start -->
Review the [CNCF Allowlist License Policy](https://github.com/cncf/foundation/blob/main/policies-guidance/allowed-third-party-license-policy.md). This governs licenses used by third-party dependencies. CNCF FOSSA or CNCF Snyk can check compliance — pick one (tracked in `license-scan-import`).
<!-- field-guide:end -->

- [x] Review and understand the CNCF Third Party License Policy <!-- checklist:license-policy-review --> (PR: [#54](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/54))

**Evidence:**

- Maintainer @clubanderson reviewed the [CNCF Allowlist License Policy](https://github.com/cncf/foundation/blob/main/policies-guidance/allowed-third-party-license-policy.md) on 2026-10-02.
- License scan service selected: FOSSA, tracked in `license-scan-import` (#11). CNCF FOSSA org import / `FOSSA_API_KEY` issuance is still pending CNCF staff action.
- Known dependency-license finding: `minimatch` resolved to BlueOak-1.0.0 in the GitHub script dependency tree; mitigation shipped in [hivecommons/hive#10178](https://github.com/hivecommons/hive/pull/10178), pinning the relevant `minimatch` resolutions to 9.0.9 (ISC). Backup exception request: [cncf/foundation#1552](https://github.com/cncf/foundation/issues/1552).
- Cheap follow-up on 2026-10-02 found no additional flagged non-allowlisted npm package licenses in `hive` lockfiles (`.github/scripts`, `dashboard`, `discord`). `go-licenses` was installed and attempted against `hive/src`, but the local toolchain emitted module/license discovery errors for first-party packages and standard-library packages, so it was not treated as authoritative. FOSSA will provide the authoritative cross-repo dependency-license scan once #11 lands.

### trademark-guidelines-review

<!-- field-guide:start -->
Review the [Linux Foundation trademark guidelines](https://www.linuxfoundation.org/trademark-usage/). Let the TOC know if you plan to change your project name.
<!-- field-guide:end -->

- [x] Review and understand the LF trademark guidelines <!-- checklist:trademark-guidelines-review --> (PR: [#46](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/46))

**Evidence:**

- Maintainer @clubanderson read and accepts the [LF trademark guidelines](https://www.linuxfoundation.org/legal/trademark-usage) as of 2026-10-02.
- Compliance spot-check: `hivecommons/hive` README, `src/README.md`, `hivecommons.dev`, and the hub portal use Linux Foundation/CNCF marks only nominatively/factually (for example, Code of Conduct and onboarding references); no CNCF logo/badge or claim beyond factual Sandbox/onboarding context was found.
- LF footer trademark sentence is tracked separately in `lf-footer` (#15); website fix PR [hivecommons/hivecommons.github.io#51](https://github.com/hivecommons/hivecommons.github.io/pull/51) is pending.
- Hive Commons project marks (`Hive Commons`, `Hive`, and the project logo) are currently held by the project/maintainers pending LF transfer, tracked in `trademark-transfer` (#33).
- Third-party marks such as GitHub, Kubernetes, Copilot, and Claude are used nominatively to identify integrations, platforms, or prerequisites; no misuse was found in the spot-check.

### trademark-transfer

<!-- field-guide:start -->
Transfer any existing trademark and logo assets to the Linux Foundation via the Project Contribution Agreement. CNCF staff sends this document to the contact emails listed in your Sandbox application.
<!-- field-guide:end -->

- [ ] Transfer trademark and logo assets to the Linux Foundation <!-- checklist:trademark-transfer --> (Issue: [#33](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/33))

**Evidence:**

_Date Contribution Agreement was signed, or status if pending._

## Review and understand other documents

### technical-leadership-principles

<!-- field-guide:start -->
Read the [Technical Leadership Principles](https://github.com/cncf/toc/blob/main/PRINCIPLES.md#technical-leadership-principles) from CNCF TOC Principles v1.0 and the [technical leadership principles enforcement guidance](https://github.com/cncf/toc/blob/main/resources/tech_leadership_principles_guidance.md), which outline expected behavior for maintainers in leadership roles.
<!-- field-guide:end -->

- [x] Review the Technical Leadership Principles <!-- checklist:technical-leadership-principles --> (PR: [#53](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/53))

**Evidence:**

- Maintainer @clubanderson reviewed the [CNCF TOC Technical Leadership Principles](https://github.com/cncf/toc/blob/main/PRINCIPLES.md#technical-leadership-principles) and [enforcement guidance](https://github.com/cncf/toc/blob/main/resources/tech_leadership_principles_guidance.md) on 2026-10-02.
- The five leaders currently bound by this for Hive are the maintainers in [hivecommons/.project maintainers.yaml](https://github.com/hivecommons/.project/blob/main/maintainers.yaml): @clubanderson, @hanthor, @Danathar, @nicholasjackson, and @kellyaa.
- Link check note: replaced the stale template URL that returned 404 and updated the LF website guidelines link to the current `policies-guidance/website-guidelines.md` path.

### project-proposal-process

<!-- field-guide:start -->
Read the [CNCF project proposal process and requirements](https://github.com/cncf/toc/blob/main/process/README.md).
<!-- field-guide:end -->

- [x] Review the project proposal process and requirements <!-- checklist:project-proposal-process --> (PR: [#51](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/51))

**Evidence:**

- Maintainer @clubanderson reviewed the [CNCF project proposal process and requirements](https://github.com/cncf/toc/blob/main/process/README.md) on 2026-10-02.
- Hive Commons was accepted as a CNCF Sandbox project on 2026-09-29 and is tracked in [cncf/sandbox#516](https://github.com/cncf/sandbox/issues/516).

### cncf-services-review

<!-- field-guide:start -->
Read about [services available to CNCF projects](https://contribute.cncf.io/resources/project-services/).
<!-- field-guide:end -->

- [x] Review services available for your project at the CNCF <!-- checklist:cncf-services-review --> (PR: [#45](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/45))

**Evidence:**

- Maintainer @clubanderson reviewed https://www.cncf.io/services-for-projects/ (and the Sandbox services summary) on 2026-10-02 — attested.

### online-program-guidelines

<!-- field-guide:start -->
Read the CNCF online program guidelines (webinars, meetups, events) provided by CNCF staff.
<!-- field-guide:end -->

- [x] Review the online program guidelines <!-- checklist:online-program-guidelines --> (PR: [#54](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/54))

**Evidence:**

- Reviewed by @clubanderson on 2026-10-02.
- Current CNCF onboarding template links the [CNCF online program guidelines](https://github.com/cncf/foundation/blob/main/policies-guidance/online-programs-guidelines.md), which returned HTTP 200 on 2026-10-02 and covers CNCF online programs including webinars and livestreams.
- Also reviewed the live [CNCF Online Programs](https://www.cncf.io/online-programs/) page (HTTP 200; title `Online Programs | CNCF`; includes webinars, meetups, and livestreams) and [Marketing Services](https://contribute.cncf.io/resources/services/marketing/) (HTTP 200; title `Marketing Services | CNCF Contributors`; includes project webinar/event support).

### telemetry-policy-review

<!-- field-guide:start -->
Read the CNCF telemetry data collection and usage policy.
<!-- field-guide:end -->

- [ ] Review the telemetry data collection and usage policy <!-- checklist:telemetry-policy-review --> (Issue: [#28](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/28))

**Evidence:**

_Confirm review complete._

### cncf-staff-office-hours

<!-- field-guide:start -->
Optional: book time with CNCF staff to walk through available resources, work through onboarding tasks together, or ask questions.
<!-- field-guide:end -->

- [x] Optional: book time with CNCF staff <!-- checklist:cncf-staff-office-hours --> (Issue: [#27](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/27))

**Evidence:**

_Meeting date, or N/A if not needed._

## Contribute and transfer other materials

### neutral-github-org

<!-- field-guide:start -->
This makes the project transferable to the CNCF's GitHub Enterprise account. If it's already in another GitHub Enterprise account, remove it from there first.
<!-- field-guide:end -->

- [x] Move the project to its own separate neutral GitHub organization <!-- checklist:neutral-github-org --> (PR: [#39](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/39))

**Evidence:**

- Verified org: [hivecommons](https://github.com/hivecommons).
- Project repositories live under the neutral org, including [hive](https://github.com/hivecommons/hive), [hivecommons.github.io](https://github.com/hivecommons/hivecommons.github.io), and this onboarding tracker. `gh repo list hivecommons --limit 100` showed all current public org repos in `hivecommons`.
- Owner check: `gh api orgs/hivecommons/members?role=admin` was permitted and returned `clubanderson` and `kellyaa`; no IBM account is visible as an org admin/owner from the permitted API response.

### ghe-invite-accepted

<!-- field-guide:start -->
CNCF will add `thelinuxfoundation` as an organization owner to ensure neutral hosting.
<!-- field-guide:end -->

- [ ] Accept the invite to join the CNCF GitHub Enterprise account <!-- checklist:ghe-invite-accepted --> (Issue: [#25](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/25))

**Evidence:**

_Date invite accepted._

### slack-migration

<!-- field-guide:start -->
CNCF staff can help. This improves discoverability, lets CNCF enforce its Code of Conduct, and enables unlimited message retention. If you already have a large Slack/Discord community, CNCF may instead link to it from a pointer channel in the CNCF Slack workspace.
<!-- field-guide:end -->

- [ ] Migrate Slack channels to the Kubernetes or CNCF Slack workspace <!-- checklist:slack-migration --> (Issue: [#24](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/24))

**Evidence:**

_Migration status or link to pointer channel._

### maintainers-circle-slack

<!-- field-guide:start -->
Join `#maintainers-circle` on CNCF Slack to find and share knowledge with other project teams.
<!-- field-guide:end -->

- [x] Join the #maintainers-circle Slack channel <!-- checklist:maintainers-circle-slack --> (PR: [#44](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/44))

**Evidence:**

- Maintainer @clubanderson (Andy Anderson) is a member of #maintainers-circle in the CNCF Slack as of 2026-10-02 (attested by maintainer).

### domain-transfer

<!-- field-guide:start -->
If your project has its own domain(s), transfer them to the CNCF. LF Contact: `projects@cncf.io`. Project Selection: CNCF.
<!-- field-guide:end -->

- [ ] Transfer project domain(s) to the CNCF <!-- checklist:domain-transfer --> (Issue: [#22](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/22))

**Evidence:**

_Domain(s) transferred, or N/A if none._

### artwork-pr

<!-- field-guide:start -->
Submit project artwork to [cncf/artwork](https://github.com/cncf/artwork). If you don't have artwork, CNCF can help design some.
<!-- field-guide:end -->

- [ ] Submit a pull request with your artwork <!-- checklist:artwork-pr --> (Issue: [#21](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/21))

**Evidence:**

_Link to the artwork PR._

### analytics-transfer

<!-- field-guide:start -->
If you use Google Analytics, add `projects@cncf.io` as an admin of your existing account so it can be moved to a CNCF-managed account. If you don't have GA, note your current analytics setup instead.
<!-- field-guide:end -->

- [ ] Transfer website analytics to the CNCF <!-- checklist:analytics-transfer --> (Issue: [#20](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/20))

**Evidence:**

_Analytics status, or N/A._

## Update and document project details

### maintainer-list-pr

<!-- field-guide:start -->
Create/verify `MAINTAINERS.md` and open a PR against the aggregated CNCF maintainer list.
<!-- field-guide:end -->

- [x] Create a maintainer list and add it to the aggregated CNCF maintainer list <!-- checklist:maintainer-list-pr --> (PR: [#52](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/52))

**Evidence:**

- Verified Hive Commons maintains CNCF project metadata in [hivecommons/.project](https://github.com/hivecommons/.project), including [maintainers.yaml](https://github.com/hivecommons/.project/blob/main/maintainers.yaml) with five maintainers: @clubanderson, @hanthor, @Danathar, @nicholasjackson, and @kellyaa.
- Also verified Hive's repository-level [OWNERS](https://github.com/hivecommons/hive/blob/v5/OWNERS) lists @clubanderson, @hanthor, and @Danathar as approvers/reviewers for the hive repo.
- The legacy aggregated CSV PR [cncf/foundation#1550](https://github.com/cncf/foundation/pull/1550) was closed because `project-maintainers.csv` is legacy for new projects; Riaan directed use of the `.project` repository on [cncf/sandbox#516](https://github.com/cncf/sandbox/issues/516#issuecomment-5957740882), and the maintainer followed up with the created `.project` repo at [cncf/sandbox#516](https://github.com/cncf/sandbox/issues/516#issuecomment-5958105966).

### maintainer-emails

<!-- field-guide:start -->
Email maintainer addresses to `project-onboarding@cncf.io` (not shared publicly). Also link each maintainer's GitHub ID with their LF profile.
<!-- field-guide:end -->

- [x] Provide maintainer emails for mailing list and Service Desk access <!-- checklist:maintainer-emails --> (Issue: [#18](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/18))

**Evidence:**

- CNCF Sandbox issue update posted with `.project` repo and LFID linking status: https://github.com/cncf/sandbox/issues/516#issuecomment-5960859194. Current LFID↔GitHub linking tracker: https://github.com/hivecommons/hive/issues/10177.

### dco-enabled

<!-- field-guide:start -->
Enable the [DCO GitHub App](https://github.com/apps/dco) on every repo in scope. A CLA may be used in addition to the DCO, not instead of it.
<!-- field-guide:end -->

- [x] Ensure the DCO app is enabled for all project GitHub repositories <!-- checklist:dco-enabled --> (PR: [#40](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/40))

**Evidence:**

- Verified 2026-10-02 with `gh repo list hivecommons`, default-branch protection checks where available, and recent merged PR checks. Each current public org repository showed a passing `DCO` check from `https://probot.github.io/apps/dco/` on recent merged PRs.
- Repo status: `hive` (#10035/#10029/#10028), `cncf-sandbox-onboarding` (#37), `hivecommons.github.io` (#45/#43/#42), `rationguard` (#116/#115/#112), `hotshot` (#116/#114/#112), `homebrew-hive` (#15/#13/#12), `dibs` (#217/#215/#214), `promptargs` (#108/#106/#104), `docs` (#172/#170/#168), `pluk` (#125/#123/#120), `spektacular` (#68/#64/#63), `.github` (#12/#11/#10), `spektacular-website` (#10/#8/#7), `hive-redirect` (#5/#4/#3), `homebrew-repo` (#2/#1), and `infra` (#8/#6/#5).
- Branch protection was readable on protected repos and includes DCO-related enforcement on `infra` (`dco`) and aggregate gates on several repos; unprotected repos were still verified through recent passing DCO PR checks.

### coc-in-readme

<!-- field-guide:start -->
Explicitly reference the CNCF Code of Conduct (or your adopted version) in the project's `README.md` on GitHub.
<!-- field-guide:end -->

- [x] Reference the CNCF Code of Conduct in README.md <!-- checklist:coc-in-readme --> (PR: [#48](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/48))

**Evidence:**

- Verified the CNCF Code of Conduct reference in [hivecommons/hive README.md](https://github.com/hivecommons/hive/blob/v5/README.md) and [src/README.md](https://github.com/hivecommons/hive/blob/v5/src/README.md) on branch `v5`.
- Verified [CODE_OF_CONDUCT.md](https://github.com/hivecommons/hive/blob/v5/CODE_OF_CONDUCT.md) adopts the CNCF Code of Conduct at https://github.com/cncf/foundation/blob/main/code-of-conduct.md.
- Verified the website repository [README.md](https://github.com/hivecommons/hivecommons.github.io/blob/main/README.md) references the CNCF Code of Conduct after [hivecommons/hivecommons.github.io#50](https://github.com/hivecommons/hivecommons.github.io/pull/50) merged; Hive root README fix was [hivecommons/hive#10039](https://github.com/hivecommons/hive/pull/10039).

### lf-footer

<!-- field-guide:start -->
Add the Linux Foundation footer to your website per [LF branding guidelines](https://github.com/cncf/foundation/blob/main/policies-guidance/website-guidelines.md). If you don't have a dedicated website, adopt these guidelines for `README.md` instead.
<!-- field-guide:end -->

- [x] Add the LF footer to your website (or README if no website) <!-- checklist:lf-footer --> (PR: [#49](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/49))

**Evidence:**

- Verified live footer on https://hivecommons.dev/ on 2026-10-02: the page includes "© 2026 The Linux Foundation / The Hive Commons authors" and the Linux Foundation trademark sentence with a link to https://www.linuxfoundation.org/trademark-usage.
- Source fix merged in [hivecommons/hivecommons.github.io#51](https://github.com/hivecommons/hivecommons.github.io/pull/51), updating the shared footer markup on the site pages.

### governance-doc

<!-- field-guide:start -->
Document written, open governance in a `GOVERNANCE.md` file at the root of your repo.
<!-- field-guide:end -->

- [x] Start a GOVERNANCE.md documenting open governance <!-- checklist:governance-doc --> (PR: [#41](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/41))

**Evidence:**

- Verified [hivecommons/hive GOVERNANCE.md](https://github.com/hivecommons/hive/blob/v5/GOVERNANCE.md).
- Summary: Hive is governed by the Hive maintainer committee; routine repository decisions use lazy consensus through GitHub review, with controversial or cross-project decisions escalated to the KubeStellar governance process.

### security-doc

<!-- field-guide:start -->
Document a security policy in a `SECURITY.md` file at the root of your repo. See [CNCF security guidelines](https://contribute.cncf.io/maintainers/security/security-guidelines/#3-securitymd).
<!-- field-guide:end -->

- [x] Start a SECURITY.md security policy <!-- checklist:security-doc --> (PR: [#42](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/42))

**Evidence:**

- Verified [hivecommons/hive SECURITY.md](https://github.com/hivecommons/hive/blob/v5/SECURITY.md).
- Reporting channel: reporters are instructed to use GitHub private vulnerability reporting from the repository Security tab; if unavailable, they may contact a repository maintainer privately.
- Additional assessment: [src/docs/security-self-assessment.md](https://github.com/hivecommons/hive/blob/v5/src/docs/security-self-assessment.md) documents the CNCF TAG-Security-style self-assessment and links the security policy.

### openssf-badge

<!-- field-guide:start -->
Register and begin working toward an [OpenSSF Best Practices Badge](https://www.bestpractices.dev/).
<!-- field-guide:end -->

- [x] Start an OpenSSF Best Practices Badge <!-- checklist:openssf-badge --> (PR: [#43](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/43))

**Evidence:**

- Verified the [OpenSSF Best Practices badge](https://www.bestpractices.dev/projects/14261) in [hivecommons/hive README.md](https://github.com/hivecommons/hive/blob/v5/README.md).
- Fetched `https://www.bestpractices.dev/projects/14261.json` on 2026-10-02: project `hive`, `badge_level` = `passing`, `tiered_percentage` = `115`, `updated_at` = `2026-09-11T13:55:59.153Z`.

### license-scan-import

<!-- field-guide:start -->
Import all repos in scope into CNCF FOSSA or CNCF Snyk (see `license-policy-review`).
<!-- field-guide:end -->

- [ ] Import all project repos into a license scanning service <!-- checklist:license-scan-import --> (Issue: [#11](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/11))

**Evidence:**

_Service used and confirmation all repos are imported._

## CNCF staff tasks (track and follow up)

These are completed by CNCF staff, not the project. Track them here so you know what to follow up on; check the box once staff confirms completion.

### devstats

<!-- field-guide:start -->
CNCF staff adds the project to [DevStats](https://all.devstats.cncf.io/).
<!-- field-guide:end -->

- [ ] CNCF staff: add the project to DevStats <!-- checklist:devstats --> (Issue: [#10](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/10))

**Evidence:**

_Link to the project's DevStats dashboard once available._

### clomonitor

<!-- field-guide:start -->
CNCF staff adds the project to [CLOMonitor](https://clomonitor.io/).
<!-- field-guide:end -->

- [ ] CNCF staff: add the project to CLOMonitor <!-- checklist:clomonitor --> (Issue: [#9](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/9))

**Evidence:**

_Link to the project's CLOMonitor report card._

### lfx-insights-onboarding

<!-- field-guide:start -->
CNCF staff adds the project to [LFX Insights](https://insights.linuxfoundation.org/).
<!-- field-guide:end -->

- [x] CNCF staff: add the project to LFX Insights <!-- checklist:lfx-insights-onboarding --> (PR: [#38](https://github.com/hivecommons/cncf-sandbox-onboarding/pull/38))

**Evidence:**

Hive is live on LFX Insights as project slug `hive`: https://insights.linuxfoundation.org/project/hive (security view: https://insights.linuxfoundation.org/project/hive/security). Confirmed by the maintainer on 2026-10-02.

### lfx-pcc-activation

<!-- field-guide:start -->
CNCF staff activates the project in the LFX Project Control Center (PCC).
<!-- field-guide:end -->

- [ ] CNCF staff: activate the project in the LFX Project Control Center <!-- checklist:lfx-pcc-activation --> (Issue: [#7](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/7))

**Evidence:**

_Confirmation date once activated._

### landscape-listing-onboarding

<!-- field-guide:start -->
After PCC activation, CNCF staff adds the project to the [Cloud Native Landscape](https://landscape.cncf.io/), including the `lfx_slug` in the landscape configuration file.
<!-- field-guide:end -->

- [ ] CNCF staff: add the project to the Cloud Native Landscape <!-- checklist:landscape-listing-onboarding --> (Issue: [#6](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/6))

**Evidence:**

_Link to the landscape PR/entry._

### license-scanner-team

<!-- field-guide:start -->
CNCF staff adds the maintainers team to the chosen license scanner service (FOSSA or Snyk).
<!-- field-guide:end -->

- [ ] CNCF staff: add the maintainers team to the license scanner <!-- checklist:license-scanner-team --> (Issue: [#5](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/5))

**Evidence:**

_Confirmation maintainers have scanner access._

### groupsio-list

<!-- field-guide:start -->
CNCF staff creates a groups.io maintainer list for the project in the LFX Project Control Center.
<!-- field-guide:end -->

- [ ] CNCF staff: create a groups.io project maintainer list in PCC <!-- checklist:groupsio-list --> (Issue: [#4](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/4))

**Evidence:**

_Groups.io list name/link._

### groupsio-maintainers-list

<!-- field-guide:start -->
CNCF staff adds the project's groups.io maintainer list to `maintainers@cncf.io`.
<!-- field-guide:end -->

- [ ] CNCF staff: add the project's groups.io list to maintainers@cncf.io <!-- checklist:groupsio-maintainers-list --> (Issue: [#3](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/3))

**Evidence:**

_Confirmation complete._

### welcome-email

<!-- field-guide:start -->
CNCF staff sends a welcome email confirming maintainer mailing list and Service Desk access.
<!-- field-guide:end -->

- [ ] CNCF staff: send a welcome email confirming maintainer list access <!-- checklist:welcome-email --> (Issue: [#2](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/2))

**Evidence:**

_Date welcome email received._

## Final review

### onboarding-complete

<!-- field-guide:start -->
When every item above is complete (or intentionally N/A), post a status update on your CNCF onboarding issue and ask CNCF staff to confirm and close it. Run `./scripts/generate-status-report.sh` to produce a paste-ready update, or `./scripts/generate-status-report.sh --post` to post it directly as a comment.
<!-- field-guide:end -->

- [ ] Final review: confirm all items complete and request sign-off <!-- checklist:onboarding-complete --> (Issue: [#1](https://github.com/hivecommons/cncf-sandbox-onboarding/issues/1))

**Evidence:**

_Link to the comment confirming onboarding complete, and the closed onboarding issue._
