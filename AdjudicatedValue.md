# Adjudicated Values

Teammates: **dlong37** and **dpate172**

This file settles every disagreement from both validation passes:

- **Part A:** dlong37 validating dpate172's MiniProject2. Source: `disagree.md` / `dlong37_validation_log.csv`. 19 disagreements.
- **Part B:** dpate172 validating dlong37's MiniProject2. Source: `dpate172_validation_log.csv`. 26 disagreements.

Each value was checked against the project data, not only against the two write-ups. The sources were:

- monthly time series (`commits-timeseries/`, `dpate172_commits_timeseries_*.csv`) and project stats
- commit data (`df_commit_data.csv`, `dpate172_project_summary.csv`, `dpate172_recent_commits.csv`)
- the PR, issue and commit evidence each partner cited

`AuthorValue` is always the original MiniProject2 author's value; `ValidatorValue` is the reviewer's.

## Summary

| | Disagreements | Author kept | Validator kept | Compromise |
|---|---|---|---|---|
| Part A (dpate172's projects) | 19 | 17 | 1 | 1 |
| Part B (dlong37's projects) | 26 | 1 | 23 | 2 |
| **Total** | **45** | **18** | **24** | **3** |

## Rules applied to both sides

The same rule was applied to every project, so that both logs resolve the same way. Rules 1, 2 and 6 were agreed by dlong37 and dpate172 after discussing the first draft of this file.

1. **Any month with zero commits is a gap.** The longest run of zero-commit months is the longest gap, even if it is 1-2 months and below the 3-month threshold used for `NumberOfGapsInTimeline`. Only a project with no zero-commit months at all (fhir-server, cucim, brainstorm3) gets `N/A active project`.
2. **Any commit after the longest gap counts as recovery.** HasRecovered is `Yes` whenever at least one commit follows the gap, regardless of how many commits follow, what kind they are, or whether a README says the project is archived. `Partly` is not a codebook value.
3. **WhyRecovered states what the evidence shows.** A cause is only claimed when a commit, PR or README says it; sequencing and dates must match the commit data.
4. **ActivityPattern is judged on the whole series:**
   - Annual totals and a rank trend are used for rising or declining.
   - Month-to-month variability (coefficient of variation, CV) separates steady from irregular.
   - Lag-12 autocorrelation tests for cyclical.
   - **No disputed project shows a yearly cycle:** lag-12 autocorrelation is between 0.04 and 0.16 for all nine. So `cyclical` is not upheld anywhere.
5. **RecentThemes counts one primary theme per commit, using only codebook themes.**
   - `Merging` and `Testing` are not codebook themes and map to `Other`.
   - A merge that names its PR takes that PR's theme; a bare "Merge <sha> into <sha>" record is `Other`.
   - Dependabot and other bot commits are `Automated bot contributions`, as the Coding Guide says.
   - Order is by count.
6. **CurrentStatus uses the Coding Guide's date as written: reference 2025-09-30, cutoff 2025-04-01.** A project is Active if its newest commit on or before 2025-09-30 falls on or after 2025-04-01. This also gives the same result on every CurrentStatus row the partners already agreed on, in both logs.

---

## Part A: dpate172's projects (author dpate172, validator dlong37)

### HasRecovered

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| ketch_nodepy | Partly | Yes | **Yes** | ValidatorKept | Two commits follow the 11-month gap (2023-10 to 2024-08): maintainer David Ketcheson's `1ea45f7` (SSP(5,4) coefficients) and a merge. Under rule 2 that is recovery, and `Partly` is not a codebook value. The thinness of the recovery belongs in Comments. |
| mouseland_suite2p | Yes | N/A active project | **Yes** | AuthorKept | The longest gap is 1 month (Nov 2024), which counts under rule 1. Commits resume in Dec 2024, and 347 dated commits follow. |
| stack-of-tasks_pinocchio | Yes | N/A active project | **Yes** | AuthorKept | The longest gap is 1 month (Dec 2014), which counts under rule 1. Commits resume in Jan 2015, and 11,320 dated commits follow. |
| agnwinds_python | Yes | N/A active project | **Yes** | AuthorKept | The longest gap is 2 months (Apr-May 2023), which counts under rule 1. Commits resume in June 2023, and 634 dated commits follow. |

### WhyRecovered

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| mouseland_suite2p | The return addressed registration-metric issue #1144 (`7bb28c69`) and HDF5-input issue #1149 (`2c406958`); Chris Ki confirmed those fixes in the linked issue discussions. | N/A active project | **The return addressed registration-metric issue #1144 (7bb28c69) and HDF5-input issue #1149 (2c406958), both reported before the gap; Chris Ki confirmed the fixes in the issue discussions.** | AuthorKept | Follows HasRecovered = Yes. The author's issue and commit evidence describes what resumed; neither source states why committing paused in Nov 2024. |
| stack-of-tasks_pinocchio | The first January 2015 commits revise ISAE teaching labs, followed by upstream merges, build configuration and constructor fixes; continuation of development, not an announced revival. | N/A active project | **The first January 2015 author-dated commits revise teaching labs for ISAE; subsequent commits handle upstream merges, build configuration, and initialization/constructor fixes. This is continuation of development, not a formally announced revival.** | AuthorKept | Follows HasRecovered = Yes. The author's text is accurate and already flags that the 1-month pause has no documented cause. |
| agnwinds_python | June 2023 commits add radiation-hydrodynamics output columns and grid-generation scripts (PR 1002), followed by documentation and bug fixes. | N/A active project | **June 2023 commits add radiation-hydrodynamics output columns and grid-generation scripts, followed by documentation and bug fixes; PR 1002 describes Knox Long's rad-hydro work and matches merge SHA 74679f5 in the post-gap sample.** | AuthorKept | Follows HasRecovered = Yes. The same contributors work on both sides of the gap; the cause of the two empty months is not documented. |

### ActivityPattern

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| hpparvi_pytransit | irregular | cyclical | **irregular** | AuthorKept | Annual totals range from 12 to 313 with no trend (rank correlation 0.19), monthly CV 1.67, and lag-12 autocorrelation 0.13. The bursts (2015, 2020, 2024, 2026) are 5, 4 and 2 years apart, which is not a fixed interval. |
| microsoft_fhir-server | steady | irregular | **steady** | AuthorKept | Every one of 88 months is active. Monthly CV is 0.41, the lowest of all nine disputed projects. Annual totals from 2020 to 2024 stay within about ±10% (2,776-3,369), after a 2019 ramp-up year. There is no trend and no cycle. |
| rapidsai_cucim | declining | cyclical | **declining** | AuthorKept | Lag-12 autocorrelation is 0.05, so cyclical is not supported. Annual totals fall 734 → 584 → 488 (2022-2024) with a partial rebound to 555 in 2025 (rank correlation -0.80). The decline is mild; `steady` would also be defensible if both partners prefer it. |
| agnwinds_python | irregular | cyclical | **irregular** | AuthorKept | No trend (rank correlation -0.02), monthly CV 0.77, and lag-12 autocorrelation 0.07. The peaks (2015, early 2018, mid-2019, spring 2020, 2023) are unevenly spaced. |

### CurrentStatus (rule 6)

| Project | Author | Validator | Newest commit by 2025-09-30 | **Adjudicated** | Resolution |
|---|---|---|---|---|---|
| esri_geoportal-server | Active | Inactive | 2025-07-08 (README update) | **Active** | AuthorKept |
| hpparvi_pytransit | Active | Inactive | 2025-07-22 (changelog and version bump) | **Active** | AuthorKept |
| sundmanbo_opencalphad | Active | Inactive | 2025-05-13 (example fix) | **Active** | AuthorKept |
| stack-of-tasks_pinocchio | Active | Inactive | 2025-09-29 (Dependabot PR #2774 merge) | **Active** | AuthorKept |
| microsoft_fhir-server | Active | Inactive | 2025-09-30 (PR #5168) | **Active** | AuthorKept |

All five newest commits fall on or after the 2025-04-01 cutoff. dlong37's Inactive values came from applying a 2026 reference date, which the pair has now set aside.

### RecentThemes

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| hpparvi_pytransit | Bug fixes:Documentation updates | Feature development:Bug fixes | **Bug fixes:Documentation updates** | AuthorKept | **Bug fixes (4):** TSModel accuracy (the diff corrects an overlap-area approximation), dtype fix, NumPy `ptp` fix, SciPy compatibility. **Documentation (2):** example notebook, installation docs. Making `pyrr` optional is a dependency change, which leaves only `slope_order` as a feature (1). |
| stack-of-tasks_pinocchio | Dependency updates:Automated bot contributions | Automated bot contributions:Feature development | **Automated bot contributions:Dependency updates** | Compromise | **Bot (6):** 2 Dependabot commits, 1 `github-actions[bot]` lock-file update, and the 3 merges of those PRs (rule 5). **Dependency updates (second):** "nix: add meshlab & viser." The viser work is environment and path fixes, not a new feature. This keeps the author's two themes in the validator's order. |
| microsoft_fhir-server | Bug fixes:Dependency updates | Dependency updates:Feature development | **Bug fixes:Dependency updates** | AuthorKept | **Bug fixes (4):** PR #5168 lock-wait fix, PR #5167 transaction-cancellation correction, SMART include/revinclude fix, relative-path fix. **Dependency updates (3):** human action bumps, shared-package bump, AzureAD to MS Graph migration. The Dependabot labeler bump is a bot contribution. `$docref` and the search-parameter cache service make only 2 features. |

---

## Part B: dlong37's projects (author dlong37, validator dpate172)

### HasRecovered

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| anybotics_elevation_mapping | No | Yes | **Yes** | ValidatorKept | Two commits follow the 7-month gap (Dec 2024-Jun 2025): an outside contributor's README edit (`8071ca0`) and its merge on 2025-07-31. Under rule 2 that is recovery, even though PR #269's discontinued-maintenance notice remains; that context belongs in WhyRecovered and Comments. |
| brainstorm-tools_brainstorm3 | N/A active project | No | **N/A active project** | AuthorKept | All 110 months have commits (minimum 12 per month), so there is no gap even under rule 1. `No` would wrongly imply a failed recovery. dpate172 used the same N/A value for fhir-server and cucim in his own MiniProject2. |
| langurmonkey_gaiasky | N/A active project | Yes | **Yes** | ValidatorKept | The longest gap is 1 month (Aug 2024), which counts under rule 1. langurmonkey resumes on 2024-09-03, and 643 dated commits follow. This is the same ruling as suite2p and pinocchio in Part A. |

### WhyRecovered

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| delftdata_valentine | Dependabot numpy bump landed, maintainers resumed the same day | Bot bump interrupted the gap in June 2022; humans resumed Python 3.11 / dependency / docs work in Sept 2022 | **An automated Dependabot numpy bump (6b315c67, 2022-06-22) was the only commit for 3 months; maintainers resumed on 2022-09-21 with Python 3.11 preparation and dependency updates (8e6bc2bd) and README work. No stated trigger for the human return.** | ValidatorKept | Commit data: the bot commit is dated 2022-06-22 and the first human commits 2022-09-21. "Same day" is not supported. |
| antonio-jp_dd_functions | Koeppe's `sage -fiximport` as part of a deprecation sweep (Jan 2025), then the original author's API cleanup (Jun 2025) | Koeppe's import changes for modularized passagemath distributions; the author's cleanup in June; causal link not established | **Matthias Koeppe ran `sage -fiximports` (bc751904, 2025-01-03; PR #23) to prepare imports for modularized passagemath distributions; in June 2025 Antonio Jimenez-Pastor returned, removing deprecated `is_*` calls and starting the PR #24 refactor. A causal link between the two is not documented.** | ValidatorKept | PR #23 describes passagemath modularization, not a deprecation sweep. The June commits do remove deprecated `is_PolynomialRing` / `is_Matrix` checks, so both partners' facts appear, with the motive corrected. |
| anybotics_elevation_mapping | N/A | Contributor README update; no return of maintenance | **Outside contributor kunj1302 (Kunj Golwala) updated the README's ROS 1 installation guidance to use grid_map's melodic-devel branch (8071ca0a, 2025-07-31); this is limited documentation activity, and PR #269's Nov 2024 notice that maintenance is discontinued still stands.** | ValidatorKept | Follows HasRecovered = Yes. The validator's text matches the commit data: one README commit and its merge, no code changes, by someone outside the original team. |
| opensafely_antibody-and-antiviral-deployment | New contributor Rose Higgins in Feb 2024; long COVID codelists suggest a new research question | Higgins restarted with codelist updates and refreshed data; long COVID role in the restart is uncertain | **New contributor Rose Higgins restarted the project in Feb 2024 with codelist updates (PR #60 "February_test_run", PR #61) and a report refresh with updated data (64e3201b, 2024-02-29); a long COVID extension followed from 2024-03-20 (d6a88c8f) but post-dates the restart.** | Compromise | Higgins is new: the pre-gap authors are bangzheng2217 and Linda Nab, which supports the author. Long COVID first appears 5 weeks after the restart, which supports the validator. |
| langurmonkey_gaiasky | N/A active project | Routine maintenance after a brief pause | **The same maintainer (langurmonkey) resumed on 2024-09-03 with a download-table documentation update (58fafb9), then frame-buffer and post-processing refactors on 2024-09-05 and a vulnerable-library update on 2024-09-09; no explicit trigger is documented, so this is routine continuation after a brief pause.** | ValidatorKept | Follows HasRecovered = Yes. The README is unchanged across the gap, and the README directs issues to Codeberg, so GitHub issues give no cause. |
| jump-dev_sumofsquares.jl | Same maintainer resumed the same work | A contributor's docs PR prompted the return, then the maintainer's tutorial | **Activity resumed with an outside contributor's docs corrections (Zdeněk Hurák, d01c1a23, merged as PR #254 on 2022-08-12), followed by maintainer Benoît Legat's obstacles tutorial (47fbe4bc, 2022-08-20); routine continuation with no documented trigger.** | Compromise | The first post-gap commit is Hurák's, so "same maintainer" is incomplete. "Prompted" overstates a causal link; the README and messages give none. |

### ActivityPattern

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| delftdata_valentine | steady | declining | **declining** | ValidatorKept | Annual totals: 205 (2020) → 70 → 31 → 54 → 42 (2024). The last-3-year mean is 42% of the first-3-year mean. 29 of 77 months have zero commits, and monthly CV is 2.31, so it is not steady. |
| darioizzo_geodesynets | steady | declining | **declining** | ValidatorKept | 133 commits in 2021, then 6, 1 and 8 in 2022-2024. 41 of 61 months are empty. The Dec 2024 recovery adds only 15 commits. |
| singmann_afex | cyclical | declining | **declining** | ValidatorKept | 116-151 commits per year in 2017-2020 (except 74 in 2019), falling to 29, 28 and 14 in 2022-2024 (rank correlation -0.67, p = 0.05). Lag-12 autocorrelation is 0.16, and peaks fall in varying months. |
| brainstorm-tools_brainstorm3 | cyclical | rising | **rising** | ValidatorKept | Annual totals: 597 (2017) → 815 → 901 (2022) → 1,264 (2024). Fitted slope is +56 commits/year, and the last-3-year mean is 1.34× the first. There is one dip (669 in 2023). Lag-12 autocorrelation is 0.10, so no yearly cycle. |
| langurmonkey_gaiasky | steady | irregular | **irregular** | ValidatorKept | No trend (rank correlation 0.09), but monthly CV is 1.03, with spikes of 318 (Aug 2017) and 667 (Jun 2021). Annual totals swing from 461 to 1,185. That variability is far above fhir-server's (CV 0.41), which was ruled steady. |

### CurrentStatus (rule 6)

| Project | Author | Validator | Newest commit by 2025-09-30 | **Adjudicated** | Resolution |
|---|---|---|---|---|---|
| darioizzo_geodesynets | Inactive | Active | 2025-09-16 (README update `9d445ab`) | **Active** | ValidatorKept |
| antonio-jp_dd_functions | Inactive | Active | 2025-06-12 (`xgcrd`, `a551545` on `develop`) | **Active** | ValidatorKept |
| anybotics_elevation_mapping | Inactive | Active | 2025-07-31 (README `8071ca0` and merge) | **Active** | ValidatorKept |
| singmann_afex | Inactive | Active | 2025-08-26 (merge `957913c`) | **Active** | ValidatorKept |

All four newest commits fall on or after the 2025-04-01 cutoff, so dpate172's evidence holds.
- **dd_functions:** status counts commits on the `develop` branch. dlong37's MiniProject2 notes already say real work continued there, even though GitHub's default branch was last updated in 2022.
- **elevation_mapping:** status follows the commit dates only, so it is Active even though maintenance is officially discontinued.

### RecentThemes

All 8 of dlong37's values either used non-codebook themes (`Merging`, `Testing`) or were outranked by a commit count. The counts below are from the 10 most recent commits in `df_commit_data.csv`.

| Project | Author | Validator | **Adjudicated** | Resolution | Basis |
|---|---|---|---|---|---|
| delftdata_valentine | Bug fixes:Documentation updates | Bug fixes:Other | **Bug fixes:Other** | ValidatorKept | **Bug fixes (4):** wheel/jar fix, publish action fix, `test_metrics` fix, small fixes. **Other (3):** tests/refactor PR #77, add tests, remove unused variable. **Documentation (2).** **Release (1):** version bump. |
| antonio-jp_dd_functions | Feature development:Testing | Other:Feature development | **Other:Feature development** | ValidatorKept | **Other (6):** PR #24 refactor merge, module rename, 3 benchmark commits, CI. **Feature (4):** `xgcrd`, sparse Ore operators, operators file, `doperators` methods. There are no test commits; `Testing` is not a codebook theme. |
| anybotics_elevation_mapping | Merging:Documentation updates | Other:Documentation updates | **Other:Documentation updates** | ValidatorKept | **Other (5):** 4 bare merges plus a package deprecation. **Documentation (3):** two README commits and the PR #269 discontinuation notice. **Release (2).** This matches the author's intent once `Merging` is mapped to `Other`. |
| singmann_afex | Bug fixes:Release | Bug fixes:Documentation updates | **Bug fixes:Documentation updates** | ValidatorKept | **Bug fixes (3):** test warnings, `aes_string` → `aes()`, ggplot2 4.0.0 preparation. **Documentation (3):** GLMMadaptive example/vignettes, rebuilt docs, and the citation-metadata merge. No release commit is in the window. This is close: `Other` has 2-3 commits (formatting, deactivating `pbkrtests`, comparison plots). |
| opensafely_antibody-and-antiviral-deployment | Feature development:Merging | Feature development:Documentation updates | **Feature development:Documentation updates** | ValidatorKept | **Feature (4):** GP therapeutics graph and its PR #70 merge, data-generation script, reporting-period update. **Documentation (3):** updated coverage report, report figures/tables, released report outputs. PR merges take their PR's theme, so `Merging` does not apply. |
| sebmart_taxisimulation | Documentation updates:Feature development | Bug fixes:Documentation updates | **Bug fixes:Documentation updates** | ValidatorKept | **Bug fixes (3):** module hotfix, offline-solutions fix, online-methods fix. **Documentation (2):** two README updates. The rest are single colour tweaks, a refactor, a dependency and the Julia 1.x port merge. |
| brainstorm-tools_brainstorm3 | Bug fixes:Merging | Other:Bug fixes | **Other:Bug fixes** | ValidatorKept | **Other (5):** 4 bare merges plus "remove previous changes." **Bug fixes (3):** SNIRF fix, autocov error handling, typo. **Feature (2).** This is the same substance as the author's value once `Merging` is mapped to `Other` and ordered by count. |
| jump-dev_sumofsquares.jl | Bug fixes:Testing | Other:Bug fixes | **Other:Bug fixes** | ValidatorKept | **Other (6):** 3 test commits, a format fix, a sources config, a bare merge. **Bug fixes (2):** two "Fix" commits that repair basis handling (per the diff). **Dependency (2):** two `bump` commits. The second-place tie with Dependency updates is broken by recency. `Testing` maps to `Other`. |

---

## Remaining items to check

1. **esri_geoportal-server conflicts with the new rules.** It was not a disagreement, because both partners logged HasRecovered `No` and WhyRecovered `N/A`. But two commits follow its 8-month gap (2024-11 to 2025-06): a README update (cd9bdd2f, 2025-07-08) and an index.html update (3014a9ce). Under rule 2 it is `Yes`. For consistency with elevation_mapping, both logs could update it to `Yes` with this WhyRecovered value: *Limited repository maintenance resumed: cd9bdd2f revises retirement and successor information and 3014a9ce adjusts the project website; neither adds application functionality.* That is dpate172's original wording.
2. **RecentThemes windows for three of dlong37's projects extend past 2025-09-30:**
   - delftdata_valentine: Oct 2025
   - brainstorm-tools_brainstorm3: Nov 2025
   - jump-dev_sumofsquares.jl: Apr 2026

   Both partners compared the same snapshot window, so the adjudicated values above stand as compared. If the 2025 reference date should also limit RecentThemes, as dpate172's own `recent_commits.csv` does, these three need recounting.
3. **cucim and afex are close calls.** cucim could be `steady` instead of `declining`. afex's second theme could be `Other` instead of `Documentation updates`.
4. **dlong37's afex row.** The Notes say "The project remains active" but CurrentStatus says Inactive. Under rule 6 the Notes are correct; the adjudicated value is Active.
