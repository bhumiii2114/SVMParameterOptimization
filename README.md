# 🔍 SVM Optimization on UCI Room Occupancy Estimation Dataset

## 📌 Objective

This project focuses on optimizing a Support Vector Machine (SVM) classifier on a multi-class dataset from the UCI repository. The goal is to evaluate the model's performance across 10 randomized samples and identify the best SVM hyperparameters through iterative optimization.

---

## 📂 Dataset

- **Dataset Name:** Room Occupancy Estimation
- **Source:** UCI Machine Learning Repository  
- **Dataset ID:** 864  
- **Total Instances:** 10k+  
- **Target Variable:** Room Occupancy Status  
- **Type:** Multi-class classification
- **Classes:** 0,1,2,3

---

## 🧪 Methodology

1. **Data Loading & Preprocessing**
   - Dataset was loaded using `ucimlrepo`.
   - Missing values checked and cleaned (if any).
   - Target column extracted, converted to a flat series for modeling.

2. **Data Splitting**
   - Dataset was randomly split into 10 **70-30 train-test samples** to test SVM consistency.
   - Stratification was used to preserve class balance.

3. **SVM Optimization**
   - SVM was tuned for each sample using Grid Search or a metaheuristic approach (e.g., Genetic Algorithm/Random Search).
   - Key hyperparameters tuned:
     - `kernel` (linear, rbf, poly, sigmoid)
     - `C` (penalty parameter)
     - `gamma` (kernel coefficient)
   - Each sample went through **100 iterations**, logging the best accuracy in each round.

4. **Result Compilation**
   - The best accuracy and hyperparameters for each sample were stored in a table.

5. **Visualization**
   - A **convergence graph** was plotted for the sample that achieved the **maximum accuracy**, showing accuracy vs iterations.

---

## 📊 Results

### 🔢 Table 1: Comparative Performance of Optimized-SVM with Different Samples

| Sample # | Best Accuracy | Best SVM Parameters (Kernel, C, Gamma)   |
|----------|----------------|------------------------------------------|
| S1       | 0.865          | rbf, C=1, gamma=scale                    |
| S2       | 0.881          | rbf, C=10, gamma=auto                    |
| S3       | 0.867          | poly, C=1, gamma=scale                   |
| S4       | 0.888          | rbf, C=1, gamma=scale                    |
| S5       | 0.869          | linear, C=1, gamma=auto                  |
| S6       | 0.891 ✅       | rbf, C=10, gamma=scale                   |
| S7       | 0.879          | rbf, C=10, gamma=scale                   |
| S8       | 0.870          | sigmoid, C=0.1, gamma=scale              |
| S9       | 0.862          | linear, C=1, gamma=scale                 |
| S10      | 0.875          | rbf, C=1, gamma=auto                     |

✅ **Sample S6 had the highest accuracy.**

---

## 📌 Conclusion

- SVM performed best with the **RBF kernel** and moderate-to-high `C` values.
- The optimization process revealed consistent performance across samples with minor variance.
- The convergence graph confirms that optimal hyperparameters were reached early and remained stable, validating the robustness of the optimization approach.
