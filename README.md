# Cycling Performance Analysis

This repository contains the complete and reproducible statistical analysis for an applied study of rider performance in a professional cycling tour. The analysis examines how rider specialization and stage characteristics relate to both the probability of scoring points and the magnitude of points scored.

---

**Note:** Due to a GitHub rendering issue, the Jupyter Notebook (`cycling_mixed_effects.ipynb`) may not display correctly in the GitHub web interface.  
The PDF provides a fully rendered and reliable version of the complete analysis.

The notebook and the PDF correspond **exactly** to the results reported in the final written report.


---

## Dataset

- **File:** `cycling.txt`
- **Unit of observation:** Rider–stage combination
- **Key variables:**
  - `rider`
  - `rider_class` (All Rounder, Climber, Sprinter, Unclassed)
  - `stage`
  - `stage_class` (flat, hills, mountain)
  - `points`

The dataset contains no missing values and exhibits a crossed repeated-measures structure, with riders observed across multiple stages.

---

## Analysis Overview

### Descriptive Analysis
- Overall distribution of points
- Grouped summaries by:
  - Rider class
  - Stage class
  - Rider class × stage class
- Visualizations:
  - Histogram of points
  - Boxplots by stage class split by rider class
  - Heatmaps of mean points and probability of scoring

### Inferential Analysis

Because the response variable (`points`) is zero-inflated and right-skewed, inference is based on a **two-part mixed-effects modeling framework**:

#### Part A: Probability of Scoring
- Mixed-effects logistic regression on `1(points > 0)`
- Fixed effects:
  - Rider class
  - Stage class
  - Rider class × stage class interaction
- Random intercepts:
  - Rider
  - Stage
- Planned contrasts with Holm adjustment

#### Part B: Magnitude of Points (Conditional on Scoring)
- Linear mixed-effects model on `log(points)` for `points > 0`
- Same fixed and random effects structure as Part A
- Results expressed as ratios of geometric means
- Residual diagnostics (QQ plot) used to assess normality on the log scale

#### Robustness Check
- Stage-level permutation test for the rider class × stage class interaction
- Test statistic: F-statistic from a fixed-effects model
- Permutation distribution visualized via histogram

---

## Analysis Files

- **Jupyter Notebook:** `cycling_mixed_effects.ipynb`  
  Contains the complete, executable analysis workflow.

- **PDF Export:** `cycling_mixed_effects.pdf`  
  A direct export of the executed notebook containing:
  - All analysis code
  - All outputs and tables
  - All figures and diagnostic plots
  - All inferential results

---

## Dependencies

The analysis was conducted in Python using:

- `numpy`
- `pandas`
- `scipy`
- `matplotlib`
- `seaborn`
- `statsmodels`

---

## Reproducibility

Running the notebook `cycling_mixed_effects.ipynb` reproduces:
- All descriptive tables
- All figures included in the report
- All inferential results and diagnostics

No manual data preprocessing is required.

---

## Notes

This repository reflects the **final version** of the analysis used in the submitted report.  
Exploratory or alternative methods tested earlier are intentionally excluded to ensure full consistency between the code, outputs, and the report.
