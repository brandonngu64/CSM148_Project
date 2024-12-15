Data Set and Overview

This project utilizes the “DoorDash ETA Prediction” dataset provided on Kaggle. The aim is to analyze the relationship between order fulfillment time and key predictor variables. The dataset contains many features that influence the estimated time for orders to be completed, including the total busy dashers, number of items in an order, and total outstanding orders. Understanding and modeling the relationship between these features and the estimated time to complete an order will help us make better predictions of delivery times. 

Methodology

Tree-Based Model:
In this project, we aimed to predict the estimated delivery time for DoorDash orders by leveraging the provided dataset, which contains numerous features influencing delivery fulfillment. The approach focused on analyzing relationships among key predictor variables such as total outstanding orders, on-shift dashers, and estimated order durations. 

The project began with data preprocessing, where efforts were made to clean the dataset by replacing infinite values with NaN and imputing these missing values with column means. Additionally, back-transformations (using np.expm1) were applied to ensure that the predictions were interpretable in their original scale rather than transformed logarithmic scales. After this, the dataset was split into a training set (75%) and a testing set (25%) using the train_test_split function. This split allowed us to train the model on one portion of the data and validate its performance on an unseen test portion.

The core methodology relied on the RandomForestRegressor, an ensemble method that we used to capture the non-linear relationships among multiple predictor variables. Hyperparameters were set with 100 estimators, a maximum depth of 15, and parameters for min_samples_split and min_samples_leaf both set to 6.





Results

After training the RandomForest model on the dataset, we evaluated its performance using Root Mean Square Error (RMSE), Mean Absolute Error (MAE), and R². On the training set, the RMSE was 0.2477, and on the testing set, it was 0.2957, which suggests good predictive performance. The MAE values were 0.1934 for training and 0.2325 for testing, indicating that the average absolute difference between predicted and actual delivery times was reasonably low. However, the R² values showed more variance, with 0.516 for training and 0.321 for testing, suggesting that while the model fits the training data well, it struggles to generalize to unseen data, a typical sign of overfitting. The Mean Absolute Error (MAE) on the original scale was 543.57 for training and 652.59 for testing. These values indicate the average absolute difference between the actual and predicted delivery times, measured in seconds. While these numbers seem large, they reflect the scale of delivery durations where a few seconds of discrepancy can have significant operational implications. The Root Mean Square Error (RMSE) was 753.82 for training and 888.59 for testing. The higher RMSE on the testing set compared to the training set suggests that the model struggles more to generalize accurately across unseen data.

The model also provided valuable insights into feature importance, which were critical in understanding the delivery time predictions. Key predictors identified included estimated store-to-consumer driving duration, total outstanding orders, and subtotal amount, which emerged as the top three influential features. These insights can help optimize delivery operations by prioritizing factors that significantly impact delivery efficiency.


While the RandomForestRegressor method worked well for this problem, its main limitation lies in its black-box nature, which restricts interpretability.

