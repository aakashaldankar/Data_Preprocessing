# Data Leakage in Machine Learning

## 1. What is Data Leakage?

Data Leakage in machine learning occurs when information from outside the training dataset is inadvertently used during model training. This external information gives the model access to data it wouldn't normally have in a real-world scenario, leading to overly optimistic performance metrics. Essentially, it is a situation where the model learns from irrelevant or future data, which corrupts the training process and invalidates the model's reliability.

## 2. How Does Data Leakage Occur?

Data leakage can occur due to various reasons during the data preparation phase. Here are some common examples:

1. **Inclusion of Future Data**: When data that should only be available after the prediction is included during training, the model learns from future events that it would not have access to during actual predictions.
2. **Incorrect Data Splitting**: Applying data preprocessing steps like scaling or normalizing to the entire dataset before splitting into training and test sets can lead to information leakage between these sets.
3. **Inappropriate Feature Selection**: Using features highly correlated with the target variable but irrelevant in real-world predictions can result in leakage, as the model uses this irrelevant data to make predictions.

## 3. How Does Data Leakage Affect Machine Learning Models?

The impacts of data leakage are significant and can lead to:

- **Overly Optimistic Performance**: Leakage causes models to perform exceptionally well during training but fail in real-world scenarios.
- **Poor Generalization**: Models trained on leaked data struggle to generalize to unseen data, producing unreliable predictions.
- **Resource Wastage**: Detecting and fixing leakage requires retraining the model, which is time-consuming and computationally expensive.
