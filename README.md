# Grading Lumbar Foraminal Stenosis — Interrater Reliability Before/After Education (Stata 17)

## Overview
This project analyses interrater agreement in MRI grading of lumbar foraminal stenosis across three timepoints:
- **Baseline**
- **Post 1 week**
- **Post 6 weeks**

The goal is to quantify how agreement changes following education on a standardized grading scale, supporting interpretation for a manuscript submission.

## My role
Health Data Analyst / Statistician 
- Built a reproducible analysis pipeline in **Stata 17**
- Prepared REDCap longitudinal data for analysis 
- Performed categorical variable coding/labeling and derived index variables
- Computed interrater agreement metrics and compared them across timepoints
- Prepared statistical outputs and contributed to manuscript results discussion

## Timepoints and comparison logic
Agreement was computed using **Gwet’s AC1** and **Krippendorff’s alpha**, and compared across timepoints.

Key comparison approach (timepoint effects):
- Compute agreement for each timepoint using:
  - `kappaetc rater1-rater9 if type=="baseline", wgt(ordinal)`
  - `kappaetc rater1-rater9 if type=="post1", wgt(ordinal)`
  - `kappaetc rater1-rater9 if type=="post2", wgt(ordinal)`
- Then compare baseline vs follow-ups using stored groups and equivalence tests.

Included headline comparisons:
- **Baseline vs 1-week post**
- **Baseline vs 6-weeks post**
- **1-week post vs 6-weeks post** (no significant change)

## Methods 
- Data preparation:
  - reshape REDCap data from **wide format** to **long format** for analysis
  - define categorical grading levels (None, Mild, Moderate, Severe)
  - align rater variables to the required agreement analysis format
- Interrater agreement (ordinal):
  - **Gwet’s AC1** with **ordinal weighting**
  - **Krippendorff’s alpha**
- Timepoint comparison:
  - quantify changes in agreement between **baseline**, **post 1 week**, and **post 6 weeks**


## What’s in this repo
- `code/Do-list.do` — Stata 17 DO-file containing:
  - data cleaning + transformation (wide → long)
  - categorical coding / label definitions
  - interrater agreement computation:
    - **Gwet’s coefficient (ordinal weighting)**
    - **Krippendorff’s alpha**
  - timepoint comparisons across baseline, post 1-week, and post 6-weeks


## Outputs / Manuscript headlines
Manuscript headline tables and figures (from your draft) are included in:
- `docs/manuscript-headlines.pdf`

## Privacy & data sharing
- The original REDCap dataset is **not included** in this GitHub repository.
- The repository shares **analysis code** and **manuscript-level aggregated results** only.

## Software
- Stata **17**

