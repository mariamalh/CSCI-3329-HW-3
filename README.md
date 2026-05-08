# CSCI 3329 — Homework 3 Report

## 1. Dataset
- Early Stage Diabetes Risk Prediction / UCI ML Repository / 520 samples / 2 classes
- Class distribution:
|  Class   | Label | Count | Percentage |
| Positive |   1   |  320  |    61.5%   |
| Negative |   0   |  200  |    38.5%   |

## 2. Preprocessing
- Rows containing missing values were dropped to prevent the scikit algorithms from crashing. No columns were removed, all were relavent.
- The categorical features and the target value were encoded using LabelEncoder so that the dimensionality of the dataset wasn't increased.
StandardScaler was applied to all the feature variables so that features such as age did not overpower the other binary features and cause the KNN and Neural Network algorithms to not run properly.

## 3. Part 2 — Algorithm Comparison
|      Algorithm      | Mean Accuracy | Std  |
| Linear Classifier   |     0.8892    |0.466 |
| Logistic Regression |     0.9259    |0.344 |
| KNN                 |     0.9253    |0.355 |
| Gaussian NB         |     0.8896    |0.421 |
| Neural Network      |     0.9739    |0.0227| 

## 4. Part 3 — Feature Selection
- Forward selection was used because the number of features in the dataset is 16 which is too large for exhaustive search.
|      Algorithm      |                                  Best Feature Subset                                    | Mean Accuracy | Std  |
| Linear Classifier   | Gender,Polyuria,Polydipsia,weakness,Genital thrush,Itching,Irritability,delayed healing |     0.8842    |0.525 |
| Logistic Regression | Gender,Polyuria,Polydipsia,Polyphagia,delayed healing,partial paresis,Alopecia,Obesity  |     0.9164    |0.364 |
| KNN                 | Age,Gender,Polyuria,Polydipsia,Genital thrush,Itching,Irritibality,Alopecia             |     0.9456    |0.316 |
| Gaussian NB         | Age,Gender,Polyuria,Genital thrush,Itching,Irritibality,delayed healing,muscle stiffness|     0.8843    |0.426 |
| Neural Network      | Age,Gender,Polyuria,Polydipsia,Sudden weightloss,itching,delayed healing,alopecia       |     0.9744    |0.0220| 


## 5. Discussion
- Part 2 vs Part 3 comparison
- Per-algorithm observations
- Limitations and ideas for improvement
