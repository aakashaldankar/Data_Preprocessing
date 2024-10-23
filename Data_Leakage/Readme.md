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


# Effects of Data Leakage on Evaluation Metrics

Two logistic classification model are modelled to perform binary classification on a synthetic dataset. First model is designed such that it has leaked data in the training set while doing the splitting. And second model does not have any leaked data in training set as the dataset is initially splitted and then pre-processed. 

## Detailed Analysis of the Output

Model with Data Leakage During Preprocessing:
The entire dataset is standardized before splitting into training and testing sets.
This approach leaks information from the test set into the training set during preprocessing.

Model without Data Leakage:
The training and testing sets are standardized separately.
This approach ensures that no information from the test set is used during the training phase.

## Evaluation Metrics
Evaluation of the models was done using the following metrics:

Accuracy
Precision
Recall
F1 Score
ROC AUC
The results are summarized in the table below:

| Metric     | With Data Leakage | Without Data Leakage |
|------------|-------------------|----------------------|
| Accuracy   | 0.875000          | 0.875000             |
| Precision  | 0.863636          | 0.840426             |
| Recall     | 0.853933          | 0.887640             |
| F1 Score   | 0.858757          | 0.863388             |
| ROC AUC    | 0.872912          | 0.876253             |

## Analysis
Accuracy:
Both models achieved the same accuracy of 0.875000. This indicates that the overall proportion of correctly classified instances is the same for both models. However, accuracy alone is not sufficient to understand the impact of data leakage.

Precision:
The model with data leakage achieved a precision of 0.863636, while the model without data leakage achieved a precision of 0.840426.
Precision measures the proportion of true positive predictions among all positive predictions. The higher precision in the model with data leakage suggests that it is better at identifying true positives, but this could be due to the leaked information.

Recall:
The model with data leakage achieved a recall of 0.853933, while the model without data leakage achieved a recall of 0.887640.
Recall measures the proportion of true positive predictions among all actual positives. The higher recall in the model without data leakage indicates that it is better at identifying all actual positives, which is a more reliable measure of performance.

F1 Score:
The model with data leakage achieved an F1 score of 0.858757, while the model without data leakage achieved an F1 score of 0.863388.
The F1 score is the harmonic mean of precision and recall. The slightly higher F1 score in the model without data leakage suggests a better balance between precision and recall.

ROC AUC:
The model with data leakage achieved an ROC AUC of 0.872912, while the model without data leakage achieved an ROC AUC of 0.876253.
ROC AUC measures the ability of the model to distinguish between positive and negative classes. The higher ROC AUC in the model without data leakage indicates better overall performance.

## Conclusion
The metrics for the model with data leakage are slightly inflated compared to the model without data leakage. This demonstrates that data leakage can lead to misleadingly high performance metrics, which do not reflect the model's true ability to generalize to new, unseen data.

## Importance of Proper Preprocessing:

Proper preprocessing techniques are essential to ensure that the model's evaluation metrics are accurate and reliable.
This includes splitting the dataset into training and testing sets before any preprocessing steps and ensuring that no information from the test set is used during the training phase.
By following these practices, we can avoid data leakage and obtain a more realistic assessment of the model's performance.
