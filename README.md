# Cognitive State Classification from fNIRS Brain Signals

This project investigates the use of machine learning models to classify cognitive states from functional near-infrared spectroscopy (fNIRS) brain signal data. Using a single dataset, two distinct classification tasks are explored to determine if neurophysiological signals (HbO, HbR, HbT) can predict participant responses and brand recognition cues.

The core objective is to compare the performance of different models and preprocessing techniques (scaling, PCA) on high-dimensional fNIRS data.

## Project Notebooks

This repository contains two separate analyses:

1.  **`brand_first_char_classification.ipynb`**:
    *   **Objective**: To classify the first initial of a brand name ('N', 'P', or 'R') that a participant was exposed to.
    *   **Target Variable**: `Brand_First_Char`

2.  **`response_code_classification.ipynb`**:
    *   **Objective**: To classify the participant's response code (0.0, 1.0, or 2.0), which likely corresponds to their recognition or sentiment towards the stimulus.
    *   **Target Variable**: `ResponseCode`

## Methodology

Both notebooks follow a similar machine learning workflow:

1.  **Data Preprocessing**: The raw signal data from `data_ite_v1.csv` is loaded and cleaned. Irrelevant columns are dropped based on the specific classification task.

2.  **Feature Engineering**: The `brand_first_char_classification` notebook explores creating aggregate features (e.g., `sum_Hbo`, `sum_Hbr`) to summarize channel activity. The `response_code_classification` notebook uses the raw signal data as features.

3.  **Data Scaling & Dimensionality Reduction**:
    *   `StandardScaler` is applied to normalize features, preventing model bias from differing data scales.
    *   **Principal Component Analysis (PCA)** is tested as a technique to reduce feature dimensions while retaining 95% of the data variance.

4.  **Model Training & Hyperparameter Tuning**:
    *   Two powerful ensemble models are trained for both tasks:
        *   `RandomForestClassifier`
        *   `GradientBoostingClassifier`
    *   `GridSearchCV` is used to find the optimal hyperparameters for each model under different data conditions (with and without PCA).

5.  **Comparative Analysis**: Model performance is evaluated and compared across different data preparations to understand the impact of feature engineering, scaling, and dimensionality reduction.

## Results & Conclusion

The analyses across both notebooks revealed several key findings:

*   **Task-Dependent Performance**: The models performed significantly better at predicting the `ResponseCode` than the `Brand_First_Char`.
    *   **Response Code Classification**: Achieved a peak accuracy of approximately **68%** using scaled data without PCA.
    *   **Brand Initial Classification**: Reached a peak accuracy of around **48%**, also using scaled data without PCA.
    *   This suggests that the fNIRS signals in this dataset contain more discriminative information about a participant's response than about the specific brand initial they are viewing.

*   **Impact of PCA**: Applying PCA consistently **degraded** model performance for both classification tasks.
    *   For `ResponseCode` classification, accuracy dropped from 68% to ~44%.
    *   For `Brand_First_Char` classification, accuracy dropped from 48% to ~31%.
    *   This indicates that while PCA reduces dimensionality by capturing variance, it discards subtle signal information crucial for these classification tasks.

*   **Best Overall Approach**: For this dataset, using the **full set of scaled features without PCA** yielded the best results for both `RandomForestClassifier` and `GradientBoostingClassifier`.

## How to Run

1.  Clone the repository to your local machine.
2.  Install the required Python libraries. You can use the `%pip install` commands at the top of each notebook or run:
    ```bash
    pip install pandas scikit-learn seaborn matplotlib numpy
    ```
3.  Ensure the `data_ite_v1.csv` file is in the same directory as the notebooks.
4.  Open and run the cells in either `brand_first_char_classification.ipynb` or `response_code_classification.ipynb` to replicate the experiments.
