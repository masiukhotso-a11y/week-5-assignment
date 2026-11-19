# Exploratory Analysis and Interactive Visualisation of Morocco Electricity Consumption

Track 1: Data Analytics, AnalystLab Africa Experience Lab Internship Programme

**Author:** Khotso Simon Peter Masiu

## Project summary
This project analyses 52,416 electricity readings, recorded every 10 minutes from 1 January to 30 December 2017, for three zones in Morocco. It looks at consumption patterns over time, compares the zones, and checks whether temperature, humidity and wind speed are associated with consumption.

Main findings:
- Demand peaks at 20:00, almost twice the 06:00 low.
- July is about 38% higher than December, and Zone 3 is the most seasonal zone.
- Temperature is the strongest environmental factor (correlation about 0.49 per reading, 0.73 on daily averages). These are associations, not proof of causation.

## Files

| File | Description |
|---|---|
| `electricity_analysis.ipynb` | Main Jupyter Notebook with all tasks, code and charts |
| `powerconsumption.csv` | Original dataset (input) |
| `cleaned_powerconsumption.csv` | Cleaned dataset with time columns and outlier flags (21 columns) |
| `data_preparation.py` | Script that recreates the cleaned dataset from the original |
| `DATA_PREPARATION.md` | Step-by-step description of the data preparation |
| `figures/` | Saved charts (PNG) and interactive Plotly charts (HTML) |
| `Morocco_Electricity_Analysis_Report.pdf` | Short analytical report |
| `Morocco_Electricity_Insights_and_Recommendations.pdf` | Business insights and recommendations |
| `README.md` | This file |

## Requirements
- Python 3.10 or newer (64-bit)
- Packages: pandas, numpy, matplotlib, seaborn, plotly, notebook

## How to reproduce the analysis (Windows)

1. **Put the files in one folder**, for example `C:\Users\<your name>\Documents\morocco_electricity`. The folder must contain `powerconsumption.csv` and `electricity_analysis.ipynb`.

2. **Install the packages.** Open Command Prompt and run:
   ```
   python -m pip install pandas numpy matplotlib seaborn plotly notebook
   ```

3. **Open the folder in Command Prompt** (use your own path):
   ```
   cd Documents\morocco_electricity
   ```

4. **(Optional) Recreate the cleaned dataset only:**
   ```
   python data_preparation.py
   ```
   This prints the data-quality checks and writes `cleaned_powerconsumption.csv`.

5. **Start Jupyter:**
   ```
   python -m notebook
   ```
   Your browser opens. Click `electricity_analysis.ipynb`.

6. **Run everything.** Click **Kernel > Restart Kernel and Run All Cells**. The notebook:
   - loads and checks the data (Task 1),
   - cleans it and adds time columns (Task 2),
   - analyses consumption by zone, hour, day, week and month (Task 3),
   - tests relationships with temperature, humidity and wind speed (Task 4),
   - builds the charts and saves them in `figures/` (Task 5),
   - records the insights and recommendations (Task 6).

7. **Stop Jupyter** by pressing **Ctrl + C** in Command Prompt, then **y**.

Running the notebook from top to bottom takes about a minute and gives the same results every time (no random steps are used).

## Notebook structure
| Section | Content |
|---|---|
| Task 1 | Dataset understanding and inspection |
| Task 2 | Data cleaning and preparation |
| Task 3 | Electricity consumption analysis |
| Task 4 | Environmental relationship analysis |
| Task 5 | Data visualisation (Matplotlib, Seaborn, Plotly) |
| Task 6 | Business insights and recommendations |

## Key data decisions
- The CSV is read with `encoding="utf-8-sig"` to remove a hidden character at the start of the file.
- No rows were removed: the data has no missing values, duplicates or gaps in the 10-minute sequence.
- Unusual Zone 3 consumption values (1,191 readings, all in July and August) were **kept and flagged**, because they are consistent summer-evening demand peaks.
- WindSpeed has a two-level pattern (most values near 0.1 or near 5), so wind results should be treated with caution.

## Limitations
- One year of data only, so year-to-year variation cannot be separated from seasonal patterns.
- Correlation does not prove causation: season, time of day and weather change together.
- Units, zone locations and zone types are not documented.
- Holidays and special events are not marked in the data.

## Troubleshooting
| Problem | Fix |
|---|---|
| `FileNotFoundError: powerconsumption.csv` | The CSV is not in the folder Jupyter started from. Use the Jupyter **Upload** button, or run `python -m notebook` from the folder that contains the file. |
| `ModuleNotFoundError` | Run the `pip install` command in step 2. |
| Package install fails with a Rust or build error | You may have 32-bit Python. Install the 64-bit version from python.org. |
| A cell shows `[*]` for a long time | Wait up to a minute. If it stays, click **Kernel > Restart Kernel** and run the cell again. |
