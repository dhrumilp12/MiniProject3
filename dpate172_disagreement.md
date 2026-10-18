# Disagreement examples for dpate172 and dlong37

Dhrumil Patel (dpate172) and David Long (dlong37) resolved the differences through text discussion and the revised adjudication shared by David. Across the two independent reviews, 45 rows were originally marked as disagreements: 26 in dpate172's review and 19 in dlong37's review. The examples below come from dpate172's review, so David is the original MiniProject2 author and Dhrumil is the validator in each case.

## Agreed rules

1. The longest gap is the longest run of zero-commit months, including runs of one or two months. NumberOfGapsInTimeline separately counts runs of at least three months. Projects with no zero-commit month use N/A active project.
2. Any commit after the longest gap counts as recovery, including documentation-only changes. Retirement or discontinued-maintenance notices remain relevant context in the explanation.
3. WhyRecovered describes the observed sequence and distinguishes an inferred explanation from an explicitly documented trigger.
4. ActivityPattern uses the full monthly series, supported by long-term trends, variability, and the spacing of peaks. These measurements support the qualitative judgment.
5. RecentThemes selects the top two allowed categories from the latest ten commits in the source snapshot that both partners compared, ordered by count. A named PR merge takes its substantive theme; a bare merge or standalone testing activity maps to Other. Bot commits use Automated bot contributions. Recency resolves a tie when needed.
6. Currentstatus uses September 30, 2025 as the reference date. A commit on or after April 1, 2025 and on or before September 30, 2025 qualifies the project as Active.

Original author values, validator values, pre-discussion flags, and KeyEvidence remain in the validation logs. AdjudicatedValue and Comments record the discussion outcomes. Resolution durations were not tracked.

## Example 1: Documentation-only recovery in ANYbotics

**Project:** anybotics_elevation_mapping

**Field:** HasRecovered

**Initial values:** dlong37: No; dpate172: Yes.

**Adjudicated value:** Yes.

**Resolution:** ValidatorKept.

After seven empty months, December 2024 through June 2025, an outside contributor updated the README's installation instructions on July 31, 2025 ([8071ca0a](https://github.com/ANYbotics/elevation_mapping/commit/8071ca0a87bfef7feec5ea0721d4e7b8a2204d80)); the source also records a merge. The partners agreed that these commits meet the recovery rule. The [discontinued-maintenance notice](https://github.com/ANYbotics/elevation_mapping/pull/269) still stands, so the final label establishes resumed repository activity without claiming that official maintenance restarted.

## Example 2: A one-month gap in Gaia Sky

**Project:** langurmonkey_gaiasky

**Field:** HasRecovered

**Initial values:** dlong37: N/A active project; dpate172: Yes.

**Adjudicated value:** Yes.

**Resolution:** ValidatorKept.

August 2024 is the selected one-month longest gap. The same maintainer resumed on September 3, 2024 with a [download-table documentation update](https://github.com/langurmonkey/gaiasky/commit/58fafb986d13ee67757e720269d49e950cab0e88), followed by rendering refactors on September 5. The partners agreed that the three-month threshold applies to NumberOfGapsInTimeline, while recovery is assessed after the longest zero-commit run even when that run is shorter. This resolves the disagreement without changing the original gap-count definition.

## Example 3: The reference date for geodesyNets

**Project:** darioizzo_geodesynets

**Field:** Currentstatus

**Initial values:** dlong37: Inactive; dpate172: Active.

**Adjudicated value:** Active.

**Resolution:** ValidatorKept.

The source records a [README update on September 16, 2025](https://github.com/darioizzo/geodesyNets/commit/9d445abb3d6214cf6455f4ff62d5885fd08004d8). Dhrumil used the coding guide's 2025 reference date, while David had treated its year as outdated and used 2026. They agreed to use the written September 30, 2025 reference date. The September 16 commit falls inside the resulting April 1-September 30 window, making the final status Active.

## Example 4: Sequence and cause in SumOfSquares.jl

**Project:** jump-dev_sumofsquares.jl

**Field:** WhyRecovered

**Initial author value:** Same maintainer resumed the same work.

**Initial validator value:** Inferred: a contributor's documentation-correction PR prompted the first resumed activity, followed by the maintainer's tutorial work.

**Resolution:** Compromise.

**Adjudicated value:** Activity resumed with an outside contributor's docs corrections (Zdeněk Hurák, d01c1a23, merged as PR #254 on 2022-08-12), followed by maintainer Benoît Legat's obstacles tutorial (47fbe4bc, 2022-08-20); routine continuation with no documented trigger.

The contributor's [documentation-correction PR](https://github.com/jump-dev/SumOfSquares.jl/pull/254) came before the maintainer's [obstacles tutorial](https://github.com/jump-dev/SumOfSquares.jl/commit/47fbe4bccdb8f5466584c444c8406e45b11e259b). The compromise corrects the original same-maintainer-only account and removes the validator's unsupported causal word prompted. The final explanation records the observed sequence without asserting why the project resumed.

## Esri consistency corrections outside the disagreement count

In dlong37_validation_log.csv, Esri's HasRecovered and WhyRecovered rows were originally marked as agreements. The adopted documentation-only recovery rule changes the final HasRecovered value to Yes because README and website commits follow its November 2024-June 2025 gap. WhyRecovered retains Dhrumil's original explanation of limited repository maintenance. The original pre-discussion Yes flags remain intact, and these two consistency corrections are excluded from the 45 original disagreements and from the 26-row dpate172_disagreement_resolution.csv.
