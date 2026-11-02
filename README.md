# Volley_Coaches

Data and code for the paper *Do mid-season coach changes improve team performance? Evidence from rally shares in Italian professional volleyball* by Manuele Leonelli.

## Contents

| File | What it is |
|---|---|
| `volley_coaches_clean.zip` | The data set used in the paper (files listed below). |
| `volley_coach_changes_build.ipynb` | Builds the regular-season matches, the coach spells, the mid-season coach changes and the coverage table from the match files, states the rules that define a coach change, and checks that the rebuilt files are identical to those in the zip. |
| `volley_coach_changes_analysis.ipynb` | Reproduces every number, table and figure of the paper from `volley_coaches_clean.zip`. |

## Data files (inside `volley_coaches_clean.zip`)

The matches were collected from the match reports published by Lega Pallavolo Serie A (legavolley.it) and Lega Pallavolo Serie A Femminile (legavolleyfemminile.it), seasons 2013/14 to 2025/26. Every row of `matches.csv` and `team_matches.csv` lists the reports it comes from (`links`) and the head coaches as printed in them (`coach_H_raw`, `coach_A_raw`, `coach_raw`), so each match and each coach can be checked against its source. The other files are built from these two by `volley_coach_changes_build.ipynb`.

| File | Rows | Content |
|---|---|---|
| `matches.csv` | 13,455 | One row per match, all phases: date, season, league, teams, set scores, head coaches as reported, source reports |
| `team_matches.csv` | 26,910 | One row per team and match, all phases, with the head coach |
| `team_matches_regular_with_perf.csv` | 20,572 | Regular-season team-matches, numbered by date within each team-season (`t`) |
| `coach_spells.csv` | 1,160 | Matches led by each head coach with each team in each season |
| `coach_changes.csv` | 166 | Mid-season coach changes: outgoing and incoming coach, last match of the outgoing coach, first successor (caretaker or new coach) |
| `coach_returns.csv` | 4 | Stand-in coaches followed by the return of the original coach, which are not counted as changes |
| `coverage.csv` | 59 | Regular-season matches observed and expected by league and season |

## How to run

Open a notebook in Google Colab and choose Runtime, then Run all. Nothing needs editing: each notebook uses `volley_coaches_clean.zip` if it is in the working folder and otherwise downloads it from this repository. Both use only packages preinstalled in Colab (numpy, pandas, scipy, statsmodels, matplotlib). The analysis takes a few minutes and ends by downloading `coach_analysis_out.zip`.

## Output of the analysis and the paper

| File in `coach_analysis_out.zip` | In the paper |
|---|---|
| `table1_data.csv` | Table 1 |
| `table3_persistence.csv` | Table 3 |
| `table4_triggers.csv` | Table 4 |
| `table5_before_after.csv` | Table 5 |
| `table6_robustness.csv` | Table 6 |
| `figure1_event_study.pdf` / `.png` / `.tif` | Figure 1 |
| `results.json` | Every number quoted in the text |
| `decomposition.csv`, `gap_decomposition.csv`, `per_match_differences.csv`, `new_coach_type.csv`, `events_matched.csv` | Numbers quoted in the text and match-level detail |

Table 2 lists the predictors of the hazard model and contains no estimates.
