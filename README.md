# CSCI 3329 — Homework 3 Report

## 1. Dataset
- Early Stage Diabetes Risk Prediction / UCI ML Repository / 520 samples / 2 classes
- Class distribution:
<div align="center">
  
| Class | Label | Count | Percentage |
| :--- | :---: | :---: | :---: |
| Positive | 1 | 320 | 61.5% |
| Negative | 0 | 200 | 38.5% |
  
</div>

## 2. Preprocessing
- Rows containing missing values were dropped to prevent the scikit algorithms from crashing. No columns were removed, all were relavent.
- The categorical features and the target value were encoded using LabelEncoder so that the dimensionality of the dataset wasn't increased.
StandardScaler was applied to all the feature variables so that features such as age did not overpower the other binary features and cause the KNN and Neural Network algorithms to not run properly.
- A fixed seed (random_state = 42) was used for all the algorithms.

## 3. Part 2 — Algorithm Comparison
<div align="center">
  
| Algorithm | Mean Accuracy | Std |
| :--- | :---: | :---: |
| Linear Classifier | 0.8892 | 0.0466 |
| Logistic Regression | 0.9259 | 0.0344 |
| KNN | 0.9253 | 0.0355 |
| Gaussian NB | 0.8896 | 0.0421 |
| Neural Network | 0.9739 | 0.0227 |

</div>
- The best performing algorithm was the Neural Network algorithm with a 97.39% accuracy on average and the most stable algorithm with a varience of +-2.27% from fold to fold. This is likely because the neural network algorithm is best at finding non-linear patterns between variables, and the relationship between the symptoms/variables in the dataset seems to be non-linear because the linear classifier algoithm performed the worst out of all the algorithms with an accuracy of 88.92% and a varience of +-46.6% from fold to fold. The fewer number of features in the dataset allowed the KNN algorithm to perform well. 

## 4. Part 3 — Feature Selection
- Forward selection was used because the number of features in the dataset is 16 which is too large for exhaustive search.
<div align="center">
  
| Algorithm | Best Feature Subset | Mean Accuracy | Std |
| :--- | :--- | :---: | :---: |
| Linear Classifier | Gender, Polyuria, Polydipsia, weakness, Genital thrush, Itching, Irritability, delayed healing | 0.8842 | 0.0525 |
| Logistic Regression | Gender, Polyuria, Polydipsia, Polyphagia, delayed healing, partial paresis, Alopecia, Obesity | 0.9164 | 0.0364 |
| KNN | Age, Gender, Polyuria, Polydipsia, Genital thrush, Itching, Irritability, Alopecia | 0.9456 | 0.0316 |
| Gaussian NB | Age, Gender, Polyuria, Genital thrush, Itching, Irritability, delayed healing, muscle stiffness | 0.8843 | 0.0426 |
| Neural Network | Age, Gender, Polyuria, Polydipsia, Sudden weightloss, itching, delayed healing, alopecia | 0.9744 | 0.0220 |

</div>

## 5. Discussion
The mean scores and the stds for the algorithms with and without optimization via feature selection shows that having less features doesn't always improve an algorithm's performance. The Neural Network algorithm remained the best performing algorithm even after optimization with little effect on its accuracy and std (average accuracy and std before: 97.39%, +-2.27%, average accuracy and std after: 97.44%, +-2.20%). The KNN algorithm had the biggest improvement in performance with its average accuracy increasing from 95.23% to 94.56% and its std decreasing from +-3.55% to +-3.16%. This is because the KNN algorithm benefits from having a constrained number of actively contributing features. On the other hand, the Logistic Regression, Linear Classifier, and Gaussian NB algorithms decreased in accuracy with the optimization. This is likely due to forward selection discarding features that contribute lightly but significantly when in combination with other features.

## 6. Reproduction
- Python version: 3.12
- scikit-learn: 1.5.1
- pandas: 2.0.3
- numpy: 2.0.2

