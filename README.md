# Multiomics Python Course – Homework Portfolio

This repository contains the short hands-on homework exercises from a Python data analysis course.  
Each class introduced one analysis concept in a lecture and then ended with a compact practical task.

The exercises are organized into topic folders:

- `Regression`
- `PCA`
- `Clustering`
- `Classifier`
- `Statistical-testing`
- `time-series-analysis`

Most tasks use small biological datasets (proteomics, lipidomics, cardiometabolic markers) and common scientific Python tools such as **pandas**, **NumPy**, **matplotlib**, **scikit-learn**, and **SciPy**.

---

## What was done in each homework

## 1) Regression (`Regression/linear-nonlinear-regression.ipynb`)

### Goal
Practice both linear and nonlinear curve fitting.

### What was implemented
- Loaded `Regression-points.xlsx` (sheet **Linear**).
- Computed linear regression parameters manually:
  - slope `m`
  - intercept `b`
- Plotted observed points and the fitted linear model.
- Calculated goodness of fit (`R²`).
- Used the model for extrapolation at `x = 10`.

Then, in the nonlinear part:
- Loaded the **Nonlinear** sheet.
- Defined a **Michaelis–Menten** model.
- Estimated parameters (`Vmax`, `Km`) with `scipy.optimize.leastsq`.
- Plotted data with the fitted nonlinear curve.
- Performed extrapolation at `x = 130`.

### Concepts practiced
Linear regression, residual-based fitting, nonlinear optimization, model visualization, and extrapolation.

---

## 2) Principal Component Analysis (`PCA/principal-component-analysis.ipynb`)

### Goal
Reduce dimensionality and interpret variance in high-dimensional proteomics data.

### What was implemented
- Loaded `MK_Proteomics.xlsx`.
- Split metadata/labels (`Day`) from numeric features.
- Standardized features with `StandardScaler`.
- Ran PCA with `sklearn.decomposition.PCA`.
- Visualized samples in PC1 vs PC2, colored by day labels.
- Reported explained variance ratios.
- Computed:
  - cumulative variance
  - number of principal components required to exceed **85% explained variance**.

### Concepts practiced
Feature scaling, unsupervised dimensionality reduction, variance interpretation, and PCA scatter plots.

---

## 3) Clustering (`Clustering/Clustering.ipynb`)

### Goal
Group samples into unsupervised clusters and visualize cluster structure.

### What was implemented
- Loaded `MK_Proteomics.xlsx`.
- Selected numeric columns only.
- Standardized all features.
- Applied **K-Means** clustering (`n_clusters=3`).
- Printed cluster assignment for each sample.
- Reduced data to 2D with PCA for visualization.
- Plotted PC1 vs PC2 and colored points by K-Means cluster label.

### Concepts practiced
Unsupervised learning, cluster assignment, preprocessing for distance-based methods, and cluster visualization.

---

## 4) Classification (`Classifier/Classifier.ipynb`)

### Goal
Compare multiple supervised classification algorithms on a tabular health dataset.

### What was implemented
- Loaded `cardio.csv` and selected 12 blood/metabolic features.
- Defined prediction target `State`.
- Trained several classifiers:
  - Decision Tree
  - Linear SVM
  - Random Forest
  - MLP (neural network)
  - Gaussian Naive Bayes
- Evaluated all models with 5-fold cross-validation using `cross_validate`.
- Printed fold-wise scores and mean accuracy per model.
- Used the trained Random Forest model to predict an **unknown sample**.

### Concepts practiced
Supervised learning workflow, model comparison, cross-validation, and inference on new observations.

---

## 5) Statistical testing (`Statistical-testing/Statistical-testing.ipynb`)

### Goal
Identify significant lipid changes between two conditions/time points.

### What was implemented
- Loaded `MK_Lipidomics.xlsx`.
- Selected lipid feature columns.
- Performed data cleaning by dropping columns with missing values in specific sample subsets.
- Split cleaned data into two groups (first 3 vs last 3 samples; day 0 vs day 7).
- Ran column-wise two-sided **Welch’s t-tests**.
- Applied multiple testing correction with **Benjamini–Hochberg FDR**.
- Built a results table with:
  - t statistics
  - raw p-values
  - adjusted p-values
- Reported top hits and number of significant lipids (`adjusted p < 0.05`).
- Visualized the distribution of uncorrected p-values with a histogram.

### Concepts practiced
Hypothesis testing in high-dimensional data, unequal-variance t-tests, false discovery control, and interpretation of significance results.

---

## 6) Time-series analysis (`time-series-analysis/series-analysis.ipynb`)

### Goal
Summarize repeated measurements over time and discover temporal profile groups.

### What was implemented
- Loaded `MK_Proteomics.xlsx`.
- Removed metadata columns and transposed the measurement matrix.
- Constructed per-feature time summaries by averaging replicates into:
  - `Day0`
  - `Day1`
  - `Day3`
  - `Day7`
- Performed hierarchical clustering on these time profiles using:
  - linkage method: average
  - distance metric: cosine
- Generated flat clusters with a high similarity threshold.
- Printed protein groups per cluster (especially larger groups).

### Concepts practiced
Time-course aggregation, profile-based clustering, cosine similarity, and hierarchical clustering interpretation.

---

## Notes

- This repository reflects **course exercises**, so notebooks are concise and focused on core concepts rather than production pipelines.
- Some notebooks embed lecture slide screenshots directly in markdown cells.
- File naming mirrors lecture numbering and topic progression.
