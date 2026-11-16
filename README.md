# Morocco Electricity Consumption and Environmental Factors Analysis

**AnalystLab Africa, Experience Lab Internship Programme, Week 5**
**Track 1: Data Analytics**
**Author:** Divine Okezie Nwaoha

## 1. Project overview

An energy management organisation in Morocco records electricity consumption every 10 minutes across three zones, alongside temperature, humidity, wind speed and two diffuse flow measurements. This project explores that data to answer:

1. What patterns exist in consumption across the three zones?
2. At which hours and on which days is consumption highest and lowest?
3. How does consumption vary across months?
4. Are temperature, humidity and wind speed associated with consumption?
5. Which zone records the highest and lowest consumption?
6. How can historical patterns support energy planning?

The analysis is done in a Jupyter Notebook using Pandas, NumPy, Matplotlib, Seaborn and Plotly.

## 2. Folder contents

```
Week 5 - Divine Okezie Nwaoha - Data Analytics/
|-- week5_morocco_electricity_analysis.ipynb   Main notebook (all six tasks)
|-- powerconsumption.csv                       Raw dataset (input)
|-- powerconsumption_datadictionary.csv        Data dictionary (input)
|-- powerconsumption_clean.csv                 Cleaned dataset (created by the notebook)
|-- charts/                                    Saved charts (PNG) and interactive Plotly charts (HTML)
|-- Week5_Analytical_Report.pdf                Short analytical report
|-- README.md                                  This file
```

Rename the notebook in the table above if your file name differs.

## 3. Requirements

- Python 3.10 or newer
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, `nbformat`, `jupyter` (or `ipykernel` if you use VS Code)

Install them with:

```
pip install pandas numpy matplotlib seaborn plotly nbformat jupyter
```

No other tools are required. Charts are saved as PNG (Matplotlib and Seaborn) and as interactive HTML (Plotly).

## 4. How to reproduce the analysis

1. Put `powerconsumption.csv` and the notebook in the same folder.
2. Open the notebook in Jupyter or VS Code.
3. Choose **Restart Kernel**, then **Run All**, so the cells run from top to bottom.
4. The notebook will:
   - load and inspect the raw data,
   - convert `Datetime` and add the Year, Month, Day, Hour, DayOfWeek and Date columns,
   - save `powerconsumption_clean.csv`,
   - produce all tables and charts and save the charts into the `charts` folder.

The data preparation steps are all in the first sections of the notebook, so the cleaned dataset can be recreated from the raw file at any time.

## 5. Data preparation summary

| Check | Result |
|---|---|
| Rows and columns | 52,416 rows, 9 columns |
| Missing values | None |
| Duplicate rows and timestamps | None |
| Recording interval | Exactly 10 minutes between all consecutive readings |
| Coverage | 1 January 2017 00:00 to 30 December 2017 23:50 (31 December is not included) |
| Zero or negative consumption | None |
| Outliers | Retained: the Zone 3 outliers are its genuine summer peak, not errors |

## 6. Key interpretation notes

- **Consumption unit.** The data dictionary labels consumption as kilowatt-hours, but the readings are in the tens of thousands per 10-minute interval, which is not plausible as energy per interval. Readings are therefore treated as average power (kW), results are reported as averages, and readings are never summed into total energy.
- **GeneralDiffuseFlows and DiffuseFlows.** The dictionary description could not be verified, so these two columns are not used for conclusions.
- **Wind speed.** Almost all readings are near 0.08 or near 4.9, so wind speed behaves like a two-level variable. Its relationship with consumption is treated with caution.
- **Correlation is not causation.** Temperature, time of day and season move together.
- **One year of data.** Patterns describe 2017 only.

## 7. Main findings

1. Demand peaks at 20:00 in all three zones and is lowest at 06:00 to 07:00.
2. July and August are the annual peak period.
3. Zone 3 is the most seasonal and variable zone.
4. Zone 1 has the highest average consumption (about 32,345 kW), then Zone 2 (about 21,042 kW) and Zone 3 (about 17,835 kW).
5. Weekend consumption is lower in Zones 1 and 2, but not in Zone 3.
6. Temperature is the environmental factor most associated with consumption, and the association is stronger in summer.

Recommendations and limitations are in section 6 of the notebook and in the PDF report.

## 8. Interactive charts

Each Plotly chart is saved twice in the `charts` folder: as a static `.png` for reports, and as an interactive `.html` file that opens in any web browser (hover for values, drag to zoom).
