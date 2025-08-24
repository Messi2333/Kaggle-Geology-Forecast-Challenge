# Geology Forecast Challenge

Project summary

- This repository contains a course project for the Kaggle competition "Geology Forecast Challenge". The task is multi-output regression: using TBM (tunnel boring machine) telemetry (priority input columns -49..0) to predict geological Z-values at positions 1..300 and to produce multiple realizations for uncertainty estimation.
- The project focuses on teaching and reproducibility. It includes detailed EDA, feature engineering ideas, and several baseline models (kNN as the primary baseline). Notebooks are provided for step-by-step reproduction.

Key files

- `Project3_Report_Complete.ipynb` — Main notebook with full EDA, data cleaning, model comparison, hyperparameter search, and final report (recommended starting point).
- `Geological_Prediction_KNN_Approach.ipynb` — Simplified, reproducible kNN-based pipeline (shorter, easier to run).
- `train_cleaned.csv`, `test_cleaned.csv` — Cleaned data copies (if present).
- `submission_*.csv` — Example submission files.
- `data/` — Raw data and helper scripts (if included).

Quick start (minimum steps)

1. Create and activate a virtual environment (macOS / bash):

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
```

2. Install Python dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly jupyterlab
```

3. Download competition data (optional if `data/` already contains the files). Using Kaggle CLI:

```bash
pip install kaggle
# Place your kaggle.json in ~/.kaggle/kaggle.json and set permissions: chmod 600 ~/.kaggle/kaggle.json
kaggle competitions download -c geology-forecast-challenge-open -p data
unzip data/*.zip -d data
```

4. Start Jupyter:

```bash
jupyter lab
# or
jupyter notebook
```

5. Recommended run order:
   - Open and run `Project3_Report_Complete.ipynb` (EDA → cleaning → features → models → generate submission)
   - For a faster baseline run, open and run `Geological_Prediction_KNN_Approach.ipynb`.

Outputs and Kaggle submission

- Notebooks will generate `submission_*.csv` files; ensure they match the `sample_submission.csv` format.
- To submit with Kaggle CLI (after configuring `kaggle.json`):

```bash
kaggle competitions submit -c geology-forecast-challenge-open -f submission_knn_best.csv -m "KNN baseline"
```

Notes and recommendations

- Use columns `-49..0` as primary input features (column 0 is normalized to 0 and typically carries no information).
- EDA documents the cleaning steps: row-wise linear interpolation for missing values in the test set, extreme-jump detection for outliers in the training set, and sliding-window feature construction. All preprocessing steps are documented in the notebooks—avoid data leakage by applying preprocessing inside cross-validation where required.
- This repo is intended for teaching and reproducibility. To improve leaderboard performance, explore advanced feature engineering, sequence models (RNN/Transformer), ensembling, and model stacking.

Contributing

- If you collaborated with teammates, add an Appendix entry in `Project3_Report_Complete.ipynb` listing each member's contribution (course requirement).
- Issues and pull requests are welcome (for example: adding `requirements.txt`, adding a `run_all.sh` script, or CI automation).

License and citation

- Consider using the MIT license for this repository. I can add a `LICENSE` file if you want.
- If you cite this work in reports or assignments, mention the project authors and course information.

Recording results

- Save your best Kaggle leaderboard screenshot into `notebooks/screenshots/` and embed it in the notebook with notes on submission date and score.
- If you want, I can also generate a `requirements.txt` and a small runner script to automate environment setup and a default notebook run.
