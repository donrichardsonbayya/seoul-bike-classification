# Objective
This project aimed to classify bike rental demand in Seoul as either high or low based on historical data and environmental factors. The dataset used comprised hourly observations collected throughout the year, including features such as weather conditions, solar radiation, temperature, time-of-day, holidays, and seasonality.

## Data Cleaning and Preprocessing
Datetime Conversion:
The Date column was transformed into multiple features like Hour, Month, and Season to better capture temporal patterns.

### Label Engineering:
The target variable High_Demand was derived by applying a median threshold to the Rented_Bike_Count column. Records above the threshold were marked as 1 (high demand), and those below as 0 (low demand).

### Handling Outliers and Scaling:
Exploratory analysis revealed outliers particularly in Wind_speed and Rainfall. While some were retained to preserve real-world variance, normalization and scaling were applied where required to ensure model robustness.

### Categorical Encoding:
Columns like Holiday and Functioning Day were converted to binary indicators. The Seasons column was label-encoded.

## Exploratory Data Analysis (EDA)
Correlation analysis was performed to identify the most influential features. It was found that Temperature, Hour, and Solar Radiation had strong positive relationships with demand, while Humidity and Rainfall showed negative correlations.

Demand trends were observed to peak during mid-day hours and during warmer seasons. On holidays, the demand was generally lower, indicating potential behavioral shifts in commuter usage.

Distributions and outliers in continuous features like Wind_speed and Temperature were assessed across demand levels. High-demand days had warmer temperatures and typically moderate wind conditions.

## Machine Learning Models
A binary classification approach was used to predict whether the daily demand would be high or low. Multiple machine learning models were implemented and tuned:

### Decision Tree Classifier
A basic classifier using recursive partitioning. The model was tuned using grid search for max_depth, min_samples_split, and criterion. The final decision tree showed that features like Hour, Temperature, and Season played key roles in splits.

### XGBoost Classifier
Applied with tree boosting and regularization to improve generalization. Hyperparameter tuning included learning_rate, n_estimators, and max_depth. XGBoost consistently outperformed other models in terms of accuracy and precision.

### Bagging and AdaBoost
Ensemble learners were built to improve performance over a single base estimator. Bagging aggregated the predictions of multiple decision trees, while AdaBoost focused on correcting misclassifications iteratively.

### Artificial Neural Network
A simple feed-forward neural network was implemented using Keras. It had a structure with dense hidden layers, ReLU activation, and dropout for regularization. The model was trained over 50 epochs and showed a gradual increase in validation accuracy, peaking near 82%.

## Evaluation and Results
Each model was evaluated using accuracy, precision, recall, and F1-score. The test set performance showed that:

XGBoost and Bagging were the most accurate models, both achieving about 93% classification accuracy.

Tuned Decision Tree and AdaBoost followed closely behind, slightly under 92%.

Neural Network performance was lower at 85%, likely due to limited model depth and lack of time-series temporal smoothing.

Confusion matrices were analyzed to inspect class-wise performance. All tree-based models displayed balanced precision and recall. The neural network showed slightly higher false positives and lower recall for high-demand predictions.

## Insights & Interpretability
Demand prediction is highly influenced by hour of day and temperature, indicating behavioral trends like commuting patterns and weather sensitivity.

Tree visualizations confirmed that demand spikes typically occur during midday hours, on non-holidays, and when temperatures are moderate to warm.

Ensemble models are especially effective when working with structured tabular data and moderate feature engineering.

### Tools and Libraries Used
pandas, numpy for data manipulation

matplotlib, seaborn for visualization

scikit-learn for classic ML models and preprocessing

xgboost for gradient boosting

tensorflow and keras for building neural networks

## Conclusion
This project successfully demonstrates a real-world classification problem solved using traditional and advanced machine learning approaches. The combination of exploratory insights, feature engineering, model comparison, and visual evaluation provides a comprehensive case study in ML workflow design. XGBoost emerged as the most reliable model for this binary classification task.

