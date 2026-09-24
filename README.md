# Global Power Plant Country Summary EDA

**Course:** Big Data Analysis — Week 2  
**Student name:** مجتبى محمد حسين  
**Program:** Master of Information Management Technologies (ماجستير تقنيات إدارة المعلومات)

This project investigates country-level power plant coverage, capacity concentration, distributions, fuel-associated capacity, numerical relationships, and generation reporting coverage. The notebook follows the six required EDA sections and contains explanations, code, tables, charts, and saved outputs.

## Files

| File | Purpose |
| --- | --- |
| `EDA_Homework.ipynb` | Complete executable analysis. |
| `dataset.csv` | Unmodified supplied dataset under a shorter relative filename. |
| `requirements.txt` | Packages directly used by the notebook. |
| `SUBMISSION_CHECKLIST.md` | Remaining identity, GitHub, and submission steps. |

## Dataset and attribution

The input was supplied as `global_power_plant_database_country_summary.csv`. It contains **212 rows and 61 columns**, with one row per country or territory. The supplied file has no explicit release/date metadata; this analysis does not assume a release version.

Upstream: [World Resources Institute Global Power Plant Database](https://github.com/wri/global-power-plant-database). Data license: [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/). The CSV is redistributed unchanged; only its filename is changed. Consult the [country-summary implementation](https://github.com/wri/global-power-plant-database/blob/master/utils/database_country_summary.py) for aggregation definitions. Notebook analysis code was written for this assignment.

CSV SHA-256: `63ae234463eae135c97858aa928ef17eb098fa3be53b89d6689aeb5cd1507e07`

## Main findings

- **167** countries/territories have recorded plants; **45** have zero records and missing summary metrics.
- **34,936** recorded plants account for **5,706.975 GW** in this snapshot.
- China leads recorded capacity (**1,415.067 GW**); the United States leads plant count (**9,833**).
- Mean country capacity is **34.174 GW**, compared with a median of **3.720 GW**, indicating strong right skew.
- Fuel-associated capacities overlap in **36** countries. These categories are not an additive fuel mix.
- Annual generation fields are counts of reporting plants. There are **6,417** reporting records for 2013 and **9,659** for 2019; these are not GWh totals.

The notebook quantifies correlations and reporting rates. Associations do not establish causation. Coverage varies, and these results do not describe present-day global generation or a complete current capacity census.

## Software and running instructions

Use Python 3.11 or newer with Jupyter Notebook or JupyterLab. Analysis dependencies are NumPy, Pandas, Matplotlib, Seaborn, and IPython. Standard-library imports need no separate installation. Exact tested versions appear in the notebook's first code output.

1. Download the repository using **Code → Download ZIP** and extract it.
2. Keep `dataset.csv` beside `EDA_Homework.ipynb`.
3. Open a terminal in that folder with your intended Python environment active.
4. Install the notebook dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

5. If Jupyter is not already installed, install the interface and Python kernel:

   ```bash
   python -m pip install jupyterlab ipykernel
   ```

6. Launch Jupyter:

   ```bash
   python -m jupyterlab
   ```

7. Open `EDA_Homework.ipynb`, select the Python kernel for that environment, and choose **Restart Kernel and Run All Cells**.
8. Confirm the tables and charts appear, then save the notebook with its outputs.

No online data download is needed during execution. Do not replace the input with a newer upstream release and expect identical results.

## Analysis decisions

The original 212 rows are retained in `raw` and `clean`. Capacity comparisons use the 167 rows with recorded plants. Missing values are not filled with zeros. Counts are validated and converted to nullable integers; no duplicates or large observations are deleted. Derived fields include mean recorded plant capacity, country capacity share, 2019 reporting coverage, and explicit plant-count groups.

Fuel categories include secondary fuels, so a plant may contribute to multiple categories. Reported generation coverage uses each year's count divided by the snapshot plant count; it is not an estimate of historical operational coverage. Country identifiers and category labels are excluded from correlations.

## Submission

Review the supplied identity details, add an official course code if required, and follow `SUBMISSION_CHECKLIST.md`. The required repository name is `big-data-eda-homework-01`. Use the instructor's visibility, access, deadline, and submission rules.

## Execution verification

Verified with a fresh Python kernel in a separate project folder. All code cells completed without errors; static chart outputs are saved. Original CSV SHA-256 matches the copied dataset.
