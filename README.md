# DataProfiler — Industry-Grade EDA Tool

🔗 **Live Demo: [soham-dataprofiler.streamlit.app](https://cipher-dataprofiler.streamlit.app)**

Upload any CSV or Excel file and get a full exploratory data analysis report instantly — with data quality scoring, outlier detection, bivariate analysis, AI-powered summary, and a downloadable PDF report. Built with Python and Streamlit, runs completely free on Google Colab.

---

## What it does

- **Data Quality Score** — 0 to 100 score across 5 dimensions: missing values, duplicates, constant columns, high cardinality, and skewness
- **Column Info Table** — type, non-null count, null count, null %, unique count, unique % for every column
- **Missing Value Chart** — colour-coded bar chart (red >30%, orange >10%, blue <10%)
- **Before/After dropna preview** — shows exactly how many rows are removed
- **Numeric Analysis** — mean, median, mode, std, min, max, skewness, kurtosis, quartiles, P5/P95, outlier detection (IQR), KDE + histogram + box plot per column
- **Categorical Analysis** — unique count, top values, frequency bar charts, null breakdown per column
- **Correlation Heatmap** — with top 10 strongest pairs table
- **Bivariate Analysis** — select any target column for KDE plots (numeric) and stacked bar charts (categorical), with class imbalance detection
- **Feature Recommendations** — colour-coded table: drop, impute, encode, transform suggestions per column
- **AI Summary** — plain English dataset summary using Groq's Llama 3.3 70B
- **PDF Report** — clean white background report with all stats, column summary, recommendations, and AI summary

---

## Demo

```
Upload: titanic.csv (891 rows, 12 columns)
Quality Score: 70/100 — Good
Missing: 866 cells (8.1%) — Age 19.9%, Cabin 77.1%
Outliers: Fare has 116 outliers (13%)
Target: Survived → Class imbalance: 62% No, 38% Yes
Recommendations: Drop Cabin (77% missing), encode Sex/Embarked
AI Summary: Dataset covers Titanic passenger survival...
```

---

## Quickstart

### Try it instantly
Visit **[soham-dataprofiler.streamlit.app](https://cipher-dataprofiler.streamlit.app)** — no setup, no install, just upload your CSV or Excel and explore.

---

### Step 1 — Get a free Groq API key (for local/Colab use)
1. Go to [console.groq.com](https://console.groq.com)
2. Sign up → API Keys → Create API Key
3. Copy the key

### Step 2 — Add key to Colab Secrets
1. Open notebook in Google Colab
2. Click the **key icon** in the left sidebar
3. Add new secret → Name: `GROQ_API_KEY` → paste key → toggle **Notebook access ON**

### Step 3 — Run the notebook
Open `data_profiler_colab.py` in Colab and run cells top to bottom. Upload any CSV or Excel when prompted.

---

## File structure

```
data-profiler/
│
├── data_profiler_colab.py     # Full notebook — open in Colab
├── README.md                  # This file
├── requirements.txt           # Python dependencies
└── sample_data/
    ├── titanic.csv            # Classic messy dataset for testing
    └── industry_test_data.csv # Large 5,250 row messy dataset for stress testing
```

---

## Supported file types

| Format | Support |
|---|---|
| CSV (.csv) | Full support |
| Excel (.xlsx) | Full support |
| Excel (.xls) | Full support |

---

## Data Quality Score breakdown

| Dimension | Max Score | Penalised when |
|---|---|---|
| Missing Values | 30 | >15% missing cells |
| Duplicates | 20 | >5% duplicate rows |
| Constant Columns | 20 | Any column with 1 unique value |
| High Cardinality | 15 | Categorical column >80% unique |
| Skewness | 15 | Non-binary column skewness >2 |

---

## Feature Recommendations legend

| Colour | Meaning |
|---|---|
| Red | DROP — column adds no value |
| Orange | Transform or impute before modelling |
| Green | Encode for modelling |

---

## Tech stack

- **Python** — pandas, numpy, matplotlib, seaborn
- **Streamlit** — interactive dark modern UI
- **Groq API** — free LLM inference (Llama 3.3 70B)
- **fpdf2** — PDF report generation
- **Google Colab** — free cloud runtime, no setup needed

---

## Known limitations

- AI summary uses top 4 numeric and 2 categorical columns to stay within Groq free tier limits (12,000 TPM)
- PDF charts not included — stats only (chart export coming in future)
- Very wide datasets (>100 columns) may be slow to render

---

## Contributing

This project is open for improvements. If you find a bug, have a better approach for any analysis, or want to add a new feature — feel free to fork, improve, and open a pull request. All contributions are welcome.

Ideas worth contributing:
- Datetime column auto-detection and trend plots
- Percentile table (P1, P5, P25, P50, P75, P95, P99)
- Chart export as PNG per column
- Multicollinearity flag for corr > 0.85
- Support for JSON and Parquet files

---

## Skills demonstrated

- Exploratory Data Analysis (EDA) from scratch
- Data quality assessment and scoring
- Outlier detection using IQR method
- Bivariate analysis with class imbalance detection
- LLM API integration (Groq)
- PDF report generation (fpdf2)
- Interactive Streamlit app with dark modern UI
- Google Colab deployment workflow

---

## License

MIT — free to use, modify, and share.
