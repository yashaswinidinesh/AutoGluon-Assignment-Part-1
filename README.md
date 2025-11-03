
# AutoGluon Notebooks — Regression, Multimodal, and Weather Classification

This repository contains **three runnable Jupyter notebooks** that showcase AutoGluon’s AutoML for tabular data and multimodal learning. Each notebook is self‑contained and uses short, reliable cells designed to finish quickly on Colab or a local GPU/CPU.



---

## 📦 Repository Contents

1. **California Housing Price Prediction** — `California_Housing_Price.ipynb`  
   *Task:* Tabular **regression** on the California Housing dataset (Kaggle).  
   *Metric:* **RMSE** (lower is better).  
   *Highlights:* Kaggle API download, AutoGluon `TabularPredictor`, model leaderboard, submission file creation.

2. **Tabular & Multimodal Learning** — `Tabular_and_Multimodel_Atuogluon.ipynb`  
   *Task:* Mixed demos — feature generation for tabular data, a quick tabular regression, and a **multimodal** classification example (images + text + stats; MNIST for images).  
   *Highlights:* AutoGluon’s automatic feature handling (numeric / categorical / datetime / text), leaderboard, MNIST digit classification with additional signals.

3. **USA Rainfall Prediction** — `USA_Rainfall__Prediction_AutoGluon.ipynb`  
   *Task:* Binary **classification** — predict “will it rain tomorrow?” from weather features.  
   *Metrics:* **ROC AUC**, Accuracy, Precision, Recall, F1‑score.  
   *Highlights:* Dataset via KaggleHub (or Kaggle API), `TabularPredictor` with classification presets, probability outputs.

---

## 🚀 Quick Start

### Option A — Colab
1. Upload a notebook to Colab (or open directly from your GitHub repo).  
2. For the multimodal part, set **Runtime → Change runtime type → GPU** (optional but faster).  
3. **Run all** cells. Verify a leaderboard and metric printout at the end.

### Option B — Local (Python 3.9+)
```bash
python -m venv .venv && source .venv/bin/activate   # (Windows: .venv\Scripts\activate)
python -m pip install --upgrade pip
pip install autogluon scikit-learn pandas numpy matplotlib torch torchvision kaggle kagglehub
jupyter lab
```
Open the notebook you want and run all cells.

---

## 📚 How to Run Each Notebook

### 1) California Housing Price Prediction (`California_Housing_Price.ipynb`)
- **Goal:** Predict median house value (regression).  
- **Dataset:** “California Housing Prices” (Kaggle).  
- **Metric:** RMSE.  
- **Flow:**
  1. Authenticate with Kaggle (upload `kaggle.json` when prompted).
  2. Download & unzip the dataset.
  3. Train with `TabularPredictor` (fast preset / time limit).
  4. Inspect the **leaderboard** and RMSE.
  5. (Optional) Export a submission CSV.
- **Kaggle CLI snippet (shown in the notebook):**
  ```bash
  pip install kaggle -q
  # Upload kaggle.json via Colab UI, then:
  mkdir -p ~/.kaggle && mv kaggle.json ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json
  kaggle datasets download -d camnugent/california-housing-prices -q
  unzip -o california-housing-prices.zip -d data_california
  ```

---

### 2) Tabular & Multimodal Learning (`Tabular_and_Multimodel_Atuogluon.ipynb`)
- **Part A — Feature Generation:** Demonstrates AutoML’s handling of numeric, categorical, datetime, and text features with simple missing‑value strategies.
- **Part B — Tabular Regression:** Quick run on a small dataset (California Housing from `sklearn` or Kaggle), with AutoGluon presets and leaderboard.
- **Part C — Multimodal Classification:** MNIST images combined with text tokens/statistics to form a unified table. AutoGluon builds and blends models over multiple modalities.
- **Notes:**
  - GPU recommended for the multimodal block.
  - Shows `predictor.leaderboard()` for transparent model comparison.

---

### 3) USA Rainfall Prediction (`USA_Rainfall__Prediction_AutoGluon.ipynb`)
- **Task:** Binary classification — `RainTomorrow` yes/no.  
- **Metrics:** Primary metric **ROC AUC** (robust to class imbalance) + Accuracy/Precision/Recall/F1.  
- **Flow:**
  1. Load data via **KaggleHub** (or Kaggle API).  
  2. Train with `TabularPredictor` (classification presets).  
  3. Print evaluation metrics and plot/report if included.  
  4. Output probability predictions.
- **KaggleHub one‑liner used in notebook (example):**
  ```python
  import kagglehub as kh
  path = kh.dataset_download("OWNER/DATASET_SLUG")  # replace with the exact dataset path
  ```

---

## ⚙️ Speed & Repro Tips

- **Fast preset:** use `presets=["medium_quality_faster_train"]` and `time_limit=120` seconds to guarantee completion during demos.
- **Sampling (optional):** for large CSVs, sample 30–50% for a quick pass, then rerun full data if time permits.
- **GPU toggle:** multimodal blocks benefit from GPU in Colab.
- **Reproducibility:** set a fixed `random_state` or `session_id`; keep output cells in the committed notebooks.

---

## 🧠 What AutoGluon Handles for You

- **Feature Engineering:** Type inference, encoders, and sensible defaults without manual pipelines.
- **Model Selection:** Trains a portfolio (e.g., tree‑based, linear, NN) under time constraints.
- **Hyperparameter Tuning:** Guided search when time allows.
- **Ensembling:** Bagging/stacking blends models to improve generalization.
- **Multimodal:** Unifies text, image, and tabular features under one training loop.

---

## 📁 Suggested Project Structure
```
.
├─ notebooks/
│  ├─ California_Housing_Price.ipynb
│  ├─ Tabular_and_Multimodel_Atuogluon.ipynb
│  └─ USA_Rainfall__Prediction_AutoGluon.ipynb
├─ data/                 # optional (Colab typically downloads into /content)
├─ outputs/              # optional: predictions, submission CSVs, leaderboards
└─ README.md
```

---

## 🔗 (Optional) Video Walkthrough
- Add your unlisted YouTube or Drive playlist link here. Aim for **1–2 minutes per notebook**.  
- Show: environment/runtime, `fit()` logs, **leaderboard**, printed metric(s).

---

## ✅ Submission Checklist
- [ ] Notebooks run end‑to‑end and **retain outputs**.  
- [ ] Each notebook shows a **leaderboard** and printed metric.  
- [ ] Kaggle tokens kept private; do **not** commit `kaggle.json`.  
- [ ] README updated with links/results.

---

## 📄 License & Attribution
- Datasets are subject to their respective licenses (Kaggle terms apply).  
- Code cells can be reused with attribution where required.
