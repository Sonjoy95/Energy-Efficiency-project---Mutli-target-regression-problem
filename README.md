# Building Energy Efficiency Prediction

This project focuses on building a robust machine learning model to accurately predict the energy consumption of buildings. The goal is to assist in the design of energy-efficient structures by forecasting both the **Heating Load** and **Cooling Load** based on key architectural and geometric features.

### Problem Statement
The primary challenge is to develop a machine learning model that can reliably predict two continuous target variables, `Heating Load` and `Cooling Load`, given a set of building parameters. Initial modeling revealed significant overfitting, particularly for the `Cooling_Load` target, which required a more advanced modeling strategy.

### Project Goal
The project's goal is to build a highly accurate, single machine learning model that can predict both `Heating Load` and `Cooling Load` with high precision while demonstrating strong generalization to unseen data.

---

### Methodology

The project followed a structured data science workflow:

1.  **Exploratory Data Analysis (EDA):** The dataset was analyzed to understand the distribution of features and the relationships between input variables and the two targets.
2.  **Data Preprocessing:** The data was cleaned and scaled, and the target variables were log-transformed to stabilize variance and improve model performance.
3.  **Initial Modeling & Overfitting Diagnosis:** It was discovered that while some models performed well on the training data, they struggled to generalize to the test set, indicating overfitting.
4.  **Hyperparameter Tuning:** A rigorous hyperparameter tuning process using `RandomizedSearchCV` was performed on three different base models (`XGBoost`, `LightGBM`, and `Random Forest`) to find the optimal balance between performance and generalization.
5.  **Ensemble Modeling:** A single `MultiOutputRegressor` using a `StackingRegressor` was built as the final model. This ensemble approach combines the predictions of the three base models (base Random Forest, LightGBM and tuned XGBoost) to produce a more accurate and robust final prediction.

---

### Key Findings & Results

The final single stacking regressor model was selected as the champion due to its superior performance and generalization for both targets.

| Metric | Heating Load | Cooling Load |
| :--- | :--- | :--- |
| **Test R² Score** | 0.9979 | 0.9832 |
| **Test Mean Absolute Error** | 0.3397 | 0.8314 |
| **Test Root Mean Squared Error**| 0.4694 | 1.2472 |

The model successfully explains over 99% of the variance in `Heating Load` and over 98% in `Cooling Load`, with minimal prediction errors.

### Conclusion

This project successfully developed a single, highly-performant stacking regressor that provides accurate and reliable predictions for both Heating and Cooling Loads. The project demonstrates a complete machine learning workflow, highlighting the importance of diagnosing and solving overfitting issues through advanced techniques like hyperparameter tuning and ensemble methods.

### Future Work

* Explore other advanced ensemble techniques or deep learning models for potential minor performance gains.
* Incorporate additional features, such as regional climate data or building material types, to create a more comprehensive model.
* Deploy the model as a web application or API for practical use by architects and urban planners.

---

### How to Run the Code
1.  Clone this repository.
2.  Install the required dependencies using `pip install -r requirements.txt`.
3.  Download and Run the Jupyter Notebook.

### Technologies Used
* Python
* Scikit-learn
* XGBoost
* LightGBM
* Pandas
* NumPy
* Matplotlib
* Seaborn
