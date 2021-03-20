## Predicting Loan Defaults

### Aim of the project
Create a risk assessment tool to help LendingClub, an online P2P loan provider, to understand whether an applicant is likely to pay a loan back or fall into default.

This repository contains underlaying [code](https://github.com/LenkaRo/predicting_loan_defaults/blob/main/predicting_loan_defaults.ipynb) and [data](https://github.com/LenkaRo/predicting_loan_defaults/tree/main/data) sources that I used to build a **machine learing model** (binary classifier). 

Click [here](https://github.com/LenkaRo/predicting_loan_defaults/blob/main/predicting_loan_defaults_presentation.pdf) to access the presentation.

To process data and to create the model I worked with the programming language **Python**. 

This is my final project as part of the [CodeClan's Data Analysis](https://codeclan.com/courses/data-analysis/) course training.

-

### Structure of the project - predictive analysis, classification:
####A. Pre-modeling (data processing)
1. import libraries

2. data import and exploration (summary statistics, vizualizations)

3. data cleaning: 
	- drop features (columns) with more than 50% of values missing,
	- drop features that only get populated once a loan has been granted (as model only inputs data for a new applicant)
	- drop features containing just one constant value,
drop categorical features showing high cardinality (= too many levels) that are not needed for machine learning and such as not worth further manipulation (eg. "binning")
	- drop observations (rows) with missing values
"regex" operations on Python object values (eg. get rid of '%' symbol)
	- transform data types where needed (eg. str -> float)
	- drop observations related to current loans (as model only inputs data for a new applicant)
4. feauture engineering:
	- set target variable "loan_status" as binary (0 = default, 1 = paid)
	- categorical features "binning" - lower the cardinality by binning values into eg. quartile intervals (results into just 4 levels and data less affected by outliers)
	- apply Box-cox transformation to address skeweness (make variables distribution more normal)
5. feature selection:
	- train/test split first to avoid overfitting!
	- on train and test datasets separatelly:
		- perform further feature reduction
			- based on correlation (between features, and between features and target variable)
			- based on variation
6. feature dummying
	- dummy categorical variables (models can only handle numerical features)

####B. Model building - machine learning binary classification model:
1. Logistic regression, 
2. Gaussian Naive Bayes, 
3. Random Forest

	- target variable: loan_status (binary variable)
	- feature matrix (explanatory variables): all features engineered and selected in the pre-modeling step
	- null model for cross validation
	- build models on default classification threshold 0.5 (Logistic regression, Gaussian Naive Bayes, Decision Tree, Random Forest)
	- access model performance
	- calculate metrics: accuracy, precision, sensitivity (= recall), specificity, AUC
	- visualize ROC
	- visualize sensitivity and specificity graphs by modifying the classification threshold and find the **optimal threshold**
	- compare the predictive power of adjusted models (TP and TN on confusion matrices) and choose the best model

#### C. Exploratory data analysis
- list out main features that have direct and clear impact on an applicant being likely to pay the loan or fall into default
- showcase model application on random sample of loan applicants


### Python libraries

An example of used Python libraries that were fundamental for the project - used to read in, clean, transform, analyse and visulase data, and to train the models and evaluate their performance:
 
`numpy`, `pandas`, `matplotlib.pyplot`, `seaborn`, `sklearn`


### Code examples
![](graphs/code_showcase_1.png)
<br>
<br>
![](graphs/code_showcase_2.png)
<br>
<br>
![](graphs/code_showcase_3.png)