# Random Forest Multiclass Classification

## Project Overview

This project implements a **Random Forest Classifier** for multiclass classification using the **Vehicle Silhouettes Dataset**.

The goal is to classify vehicle silhouettes into three different vehicle classes based on geometric and shape-related features.

The project also investigates the effect of different Random Forest hyperparameters on classification performance.

## Dataset

**Dataset:** Vehicle Silhouettes

The dataset contains **846 samples**, **18 input features**, and **3 target classes**:

- Bus
- Car
- Van

### Dataset Features

The dataset includes geometric and shape-related measurements such as:

- Compactness
- Circularity
- Distance Circularity
- Radius Ratio
- PR Axis Aspect Ratio
- Max Length Aspect Ratio
- Scatter Ratio
- Elongatedness
- PR Axis Rectangularity
- Max Length Rectangularity
- Scaled Variance
- Scaled Radius of Gyration
- Skewness-related features
- Hollows Ratio

## Data Preprocessing

The following preprocessing steps were applied:

1. Loaded the Vehicle Silhouettes dataset.
2. Checked the dataset for missing values.
3. Found **41 missing values** in the input features.
4. Replaced missing numerical values with the **median** of their corresponding feature.
5. Verified that there were **0 missing values** after preprocessing.
6. Separated the dataset into features (`X`) and target (`y`).
7. Split the data into:
   - **80% Training:** 676 samples
   - **20% Testing:** 170 samples
8. Used `random_state=42` and stratification to maintain class distribution.

## Random Forest Models

Five Random Forest configurations were evaluated:

1. **Random Forest Baseline**
   - `n_estimators = 100`

2. **Random Forest with n_estimators = 100**
   - `n_estimators = 100`

3. **Random Forest with max_depth = 10**
   - `n_estimators = 100`
   - `max_depth = 10`

4. **Random Forest with min_samples_split = 5**
   - `n_estimators = 100`
   - `min_samples_split = 5`

5. **Random Forest with max_features = log2**
   - `n_estimators = 100`
   - `max_features = "log2"`

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Training Time
- Confusion Matrix
- Feature Importance

## Results

| Model | Accuracy | Precision | Recall | F1-Score | Training Time |
|---|---:|---:|---:|---:|---:|
| Random Forest Baseline | 0.952941 | 0.954270 | 0.952941 | 0.953012 | 0.266764 |
| Random Forest n_estimators=100 | 0.952941 | 0.954270 | 0.952941 | 0.953012 | 0.266764 |
| Random Forest max_depth=10 | 0.952941 | 0.953361 | 0.952941 | 0.952951 | 0.286397 |
| Random Forest min_samples_split=5 | **0.958824** | **0.959500** | **0.958824** | **0.958844** | **0.193054** |
| Random Forest max_features=log2 | 0.952941 | 0.954270 | 0.952941 | 0.953012 | 0.223550 |

## Best Model

The best-performing configuration was:

**Random Forest with `min_samples_split = 5`**

Performance:

- **Accuracy:** 95.88%
- **Precision:** 95.95%
- **Recall:** 95.88%
- **F1-Score:** 95.88%
- **Training Time:** 0.193 seconds

This configuration achieved the highest Accuracy, Precision, Recall, and F1-Score among the evaluated models.

## Feature Importance

The most important features in the Random Forest model include:

1. `max.length_aspect_ratio`
2. `scaled_variance.1`
3. `elongatedness`
4. `distance_circularity`
5. `max.length_rectangularity`
6. `scatter_ratio`
7. `scaled_variance`
8. `pr.axis_aspect_ratio`

The feature `max.length_aspect_ratio` had the highest importance in the evaluated model.

## Project Structure

```text
Random-Forest-Multiclass-Classification/
│
├── 01_Random_Forest_Baseline.ipynb
├── 02_Random_Forest_N_Trees.ipynb
├── 03_Random_Forest_Max_Depth.ipynb
├── 04_Random_Forest_Min_Samples.ipynb
├── 05_Random_Forest_Max_Features.ipynb
├── 06_Random_Forest_Comparison.ipynb
├── random_forest_comparison_results.csv
└── README.md
```

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Kaggle

## Conclusion

The project demonstrates the use of **Random Forest for multiclass vehicle classification**.

Five different Random Forest configurations were evaluated and compared using multiple performance metrics.

Among the tested configurations, **`min_samples_split=5`** achieved the best overall performance with an accuracy of approximately **95.88%** and an F1-Score of approximately **95.88%**.

The results show that adjusting Random Forest hyperparameters can affect both predictive performance and training time.
