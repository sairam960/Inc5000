# INC 5000 Analysis

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB)]() [![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626)]() [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)]()

A reproducible analysis of **Inc. 5000 / Inc. 500** companies exploring growth trends, industry mix, geography, and performance patterns.  
This repository includes an executable notebook and a pre-rendered HTML report for quick viewing.

## 📊 Quick Links
- **HTML Report (exported from the notebook):** `reports/Inc5000.html`
- **Notebook:** `notebooks/Inc5000.ipynb`

> In this ChatGPT session, you can download the generated files here:  
> - [Inc5000.html](sandbox:/mnt/data/Inc5000.html)  
> - [README.md](sandbox:/mnt/data/README.md)

## 🧠 What’s inside
- Data cleaning and schema overview
- Company growth distribution and outliers
- Top industries by count and median growth
- Geographic concentration (state/city heatmaps if available)
- Revenue vs. employee growth relationships
- Year-over-year comparisons (if multiple years included)
- Simple modeling / correlation checks for growth predictors

*(Sections above reflect common analysis steps; actual contents depend on the notebook.)*

## 🗂️ Suggested repo structure
```
.
├── data/
│   ├── raw/                 # Original data (not committed if licensed)
│   └── processed/           # Cleaned / engineered datasets
├── notebooks/
│   └── Inc5000.ipynb        # Main analysis
├── reports/
│   └── Inc5000.html         # Exported HTML report
├── src/                     # Reusable helpers (optional)
│   ├── data.py
│   ├── viz.py
│   └── utils.py
└── README.md
```

> Tip: If your current files are at the repo root, feel free to keep them there. The above layout is simply a clean, conventional option.

## 🛠️ Environment & dependencies
Below are third‑party Python packages detected from the notebook:
- `matplotlib`
- `numpy`
- `pandas`
- `seaborn`

### Create a virtual environment (either works)
```bash
# using uv (fastest)
uv venv && source .venv/bin/activate
uv pip install -U pip

# or using pip
python -m venv .venv && source .venv/bin/activate
pip install -U pip
```

### Install dependencies
List the packages above in a `requirements.txt` or install individually, e.g.:
```bash
pip install matplotlib numpy pandas seaborn
```

> If your notebook uses geospatial or visualization libs (e.g., `geopandas`, `plotly`, `altair`), add them as needed.

## ▶️ Reproducibility
1. **Clone the repository**
   ```bash
   git clone <your-repo-url>.git
   cd <your-repo-name>
   ```
2. **(Optional) Place data files**
   - If source data is licensed (Inc. 5000), **do not commit it**. Store in `data/raw/` and reference via a local path or environment variable.
3. **Run the notebook**
   ```bash
   jupyter lab  # or jupyter notebook
   ```
   Open `notebooks/Inc5000.ipynb` and **Run All**.
4. **Export to HTML (CI‑friendly)**
   ```bash
   jupyter nbconvert --to html notebooks/Inc5000.ipynb --output reports/Inc5000.html
   ```

## 📈 Re-running in CI (optional)
You can auto-build the HTML report on push using GitHub Actions. Example workflow:
```yaml
name: build-report
on: [push]
jobs:
  nbconvert:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Install deps
        run: |
          python -m pip install -U pip
          pip install jupyter nbconvert matplotlib numpy pandas seaborn
      - name: Convert notebook to HTML
        run: |
          jupyter nbconvert --to html notebooks/Inc5000.ipynb --output reports/Inc5000.html
      - name: Upload artifact
        uses: actions/upload-artifact@v4
        with:
          name: inc5000-report
          path: reports/Inc5000.html
```

## 🔒 Data licensing note
The Inc. 5000/Inc. 500 dataset may be subject to licensing restrictions. Avoid committing raw data unless you have distribution rights. Consider providing instructions or scripts for authorized users to download the data locally.

## 🧾 Citation
If you use this analysis, please cite this repository. Example:
> *Your Name*. **INC 5000 Analysis**. GitHub repository, 2025.

## 📄 License
MIT © You
