#Approach Summary

This notebook demonstrates a machine learning approach to predict the sale price of bulldozers.

1.  **Data Preprocessing and Cleaning**:
    *   **Missing Value Handling**: Columns with more than 70% missing values were identified and removed from the dataset. For the remaining columns with missing data, numerical columns were imputed using the *median* of the existing values in that column, and categorical columns were imputed using the *mode* (most frequent value) in that column. This ensures that the models can handle the data without being affected by missing entries.
2.  **Feature Engineering**:
    *   **Date Feature Extraction**: The 'saledate' column, which was initially an object type, was converted into datetime objects. From this datetime column, new numerical features representing the *year*, *month*, and *day* of the sale were extracted and added to the dataset.
    *   **Outlier Handling**: An outlier in the 'YearMade' column where the year was listed as 1000 was removed. Outliers in the 'MachineHoursCurrentMeter' column were addressed by capping the values at the 99th percentile to prevent extreme values from disproportionately influencing the models.
3.  **Categorical Feature Encoding**:
    *   **One-Hot Encoding**: All categorical features (columns with 'object' data types after initial preprocessing) were converted into numerical format using one-hot encoding. This technique creates new binary columns for each unique category within a feature, allowing machine learning models that require numerical input to utilize this information.
4.  **Model Training**:
    *   **Model Selection**: Two algoritms were used for training the model: Random Forest Regressor and Gradient Boosting Regressor.
    *   **Training Process**: Both models were trained on the preprocessed training data (`X_train` and `y_train`).
5.  **Model Evaluation**:
    *   **Validation Set Evaluation**: After training, both models were evaluated on a separate validation set (`X_valid`, `y_valid`). The evaluation metric used was the Root Mean Squared Log Error (RMSLE), which is commonly used in competitions like this to penalize large errors on smaller values more than on larger values.
    *   **Benchmark Comparison**: To understand the performance of the trained models in context, their predictions on the test data were compared with the random forest benchmark file and then the RMSLE between each model's predictions and the benchmark predictions was calculated. This comparison showed how closely each of the trained models' outputs aligned with the established benchmark.
