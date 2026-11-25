# apachejit-defect-prediction

Just-in-time (JIT) defect prediction on the ApacheJIT dataset: predicting whether a commit will introduce a bug, using CatBoost, with SHAP explanations.

> **Status:** 🚧 Work in progress

---

## 1. Goal

_Write 2–3 sentences: what problem this solves, and why it matters to developers._

___

---

## 2. Dataset

- **Name:** ApacheJIT
- **Source:** https://github.com/hosseinkshvrz/apachejit (`dataset/apachejit_total.csv`)
- **Paper:** H. Keshavarz and M. Nagappan, "ApacheJIT: A Large Dataset for Just-In-Time Defect Prediction," *MSR 2022*.

### 2.1 Quick facts

| Fact | Value |
|---|---|
| Number of commits (rows) | ___ |
| Number of columns | ___ |
| Number of project values | ___ |
| Date range | ___ to ___ |
| Buggy commits | ___ (___ %) |
| Clean commits | ___ (___ %) |
| Missing values | ___ |
| Duplicate `commit_id`s | ___ |
| Sorted by date? | ___ |

**Notes:**
- _Note on how Hadoop is split across project values:_ ___
- _Note on class imbalance and what it means for evaluation:_ ___

### 2.2 Columns

Role: **Label** = what we predict · **Feature** = model input · **Not used** = ID, grouping or time info only

| Column | Meaning (in my own words) | Type | Role |
|---|---|---|---|
| `commit_id` | ___ | text | Not used (ID) |
| `project` | ___ | text | Not used (grouping) |
| `buggy` | ___ | bool | **Label** |
| `fix` | ___ | bool | Feature |
| `year` | ___ | int | Not used (time) |
| `author_date` | ___ | datetime | Not used (used for split) |
| `la` | ___ | int | Feature |
| `ld` | ___ | int | Feature |
| `nf` | ___ | int | Feature |
| `nd` | ___ | int | Feature |
| `ns` | ___ | int | Feature |
| `ent` | ___ | float | Feature |
| `ndev` | ___ | float | Feature |
| `age` | ___ | float | Feature |
| `nuc` | ___ | float | Feature |
| `aexp` | ___ | int | Feature |
| `arexp` | ___ | float | Feature |
| `asexp` | ___ | float | Feature |

---

## 3. Exploratory Data Analysis

### 3.1 Buggy vs clean: medians

| Feature | Median (buggy) | Median (clean) | Buggy higher? |
|---|---|---|---|
| `la` | ___ | ___ | ___ |
| `ld` | ___ | ___ | ___ |
| `nf` | ___ | ___ | ___ |
| `nd` | ___ | ___ | ___ |
| `ns` | ___ | ___ | ___ |
| `ent` | ___ | ___ | ___ |
| `ndev` | ___ | ___ | ___ |
| `age` | ___ | ___ | ___ |
| `nuc` | ___ | ___ | ___ |
| `aexp` | ___ | ___ | ___ |
| `arexp` | ___ | ___ | ___ |
| `asexp` | ___ | ___ | ___ |

### 3.2 Plots

**Lines added (`la`), log scale**

![Lines added histogram](figures/la_histogram.png)

_What it shows:_ ___

**Buggy rate per project**

![Buggy rate per project](figures/buggy_rate_per_project.png)

_What it shows:_ ___

**Buggy rate per year**

![Buggy rate per year](figures/buggy_rate_per_year.png)

_What it shows:_ ___

### 3.3 Key observations

1. ___
2. ___
3. ___

---

## 4. Method

### 4.1 Train / validation / test split

- **Type:** time-based (sorted by `author_date`, no shuffling)
- **Ratio:** ___ / ___ / ___

| Set | Rows | Date range | Buggy % |
|---|---|---|---|
| Train | ___ | ___ to ___ | ___ |
| Validation | ___ | ___ to ___ | ___ |
| Test | ___ | ___ to ___ | ___ |

_Why time-based and not random:_ ___

### 4.2 Preprocessing

- **Log transform:** ___ (which columns, and why)
- **Scaling:** ___ (fit on train only)
- **`fix` column:** ___
- **Class imbalance handling:** ___

### 4.3 Models

| Model | Key settings |
|---|---|
| Baseline: ___ | ___ |
| CatBoost | ___ |

### 4.4 Evaluation metrics

- Precision, Recall, F1, ROC-AUC, PR-AUC
- **PR-AUC of a random model** (= test-set buggy share): ___

---

## 5. Results

### 5.1 Test set

| Model | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|---|---|---|---|---|---|
| Random (reference) | — | — | — | 0.50 | ___ |
| Baseline: ___ | ___ | ___ | ___ | ___ | ___ |
| CatBoost | ___ | ___ | ___ | ___ | ___ |

### 5.2 Cross-validation (time-series folds)

| Model | Mean F1 (± std) | Mean ROC-AUC (± std) | Mean PR-AUC (± std) |
|---|---|---|---|
| Baseline: ___ | ___ | ___ | ___ |
| CatBoost | ___ | ___ | ___ |

_Number of folds and how they were built:_ ___

---

## 6. Explainability (SHAP)

### 6.1 Global importance

![SHAP summary plot](figures/shap_summary.png)

_Top features and what they mean:_
1. ___
2. ___
3. ___

### 6.2 One example commit

![SHAP waterfall plot](figures/shap_waterfall.png)

_Why the model flagged this commit:_ ___

---

## 7. Limitations

- **Label latency:** ___
- ___
- ___

---

## 8. How to run

1. Open the notebook in Google Colab: [apachejit_defect_prediction.ipynb](apachejit_defect_prediction.ipynb)
2. Run all cells (Runtime → Run all). The dataset is downloaded automatically from GitHub.

**Main libraries:** pandas, scikit-learn, catboost, shap, matplotlib

---

## 9. References

1. H. Keshavarz and M. Nagappan, "ApacheJIT: A Large Dataset for Just-In-Time Defect Prediction," *Proc. MSR*, 2022.
2. Y. Kamei et al., "A Large-Scale Empirical Study of Just-in-Time Quality Assurance," *IEEE TSE*, 2013.
3. ___
