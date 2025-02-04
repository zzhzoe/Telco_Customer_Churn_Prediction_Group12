# Telco Customer Churn Predictor

- Contributors: Zihan Zhou, Anupriya Srivastava, Adam Morphy, Jordan Casoli 

## About

For this project we are trying to answer the following question: given certain telecommunications customer characteristics, is a given customer likely to churn? A natural follow up question that we will also be addressing is: what customer characteristics are positively associated with high churn risk? Understanding the answers to these questions will provide actionable insights to telecommunications companies, allowing them to keep their customers for longer periods of time. Ultimately this will lead to higher customer lifetime value.

The dataset we are using comes from the public IBM github page, and is made available as part of an effort (by IBM) to teach the public how to use some of their machine learning tools. Unfortunately no mention is made of exactly how the data was collected, or who was responsible for the collection. Here is a link to the [mini-course](https://developer.ibm.com/patterns/predict-customer-churn-using-watson-studio-and-jupyter-notebooks/) that references the dataset we are using. The raw data is [here](https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv), and lives inside the data folder of the [public repository](https://github.com/IBM/telco-customer-churn-on-icp4d) for the mini-course. Each row in the dataset corresponds to a single customer. There are 19 feature columns, along with the target column, “churn”.

To begin, we will split the data into train and test sets (80% train/20% test). We will then carry out preliminary EDA on the training data. Specifically, we need to understand whether class imbalance will be an issue in our analysis. Therefore, we will present a table that shows the two class counts. For each of our categorical/binary features, distributions across our two classes will be plotted as stacked bar charts. For each of our numeric features, distributions across our two classes will be plotted as stacked density charts.

At a high level, our plan to answer the predictive question stated above is to build a predictive classification model. We will focus on models that give some indication as to which features are positively or negatively associated with our target class (ex. A logistic regression model), as this is an important aspect of the overall problem. Our primary objective is to be able to identify customers who are at high risk of churning, therefore we will build a model that aims to reduce type II error at the expense of possibly committing more type I error.

We will perform hyperparameter optimization, and then fit the best model on our train data before evaluating the model on our test set. At this point we will assess our final model performance using some combination of recall, precision, roc auc, and average precision. We will present a confusion matrix corresponding to our test results as a table in the final report. Finally, we will present a table showing the features most positively correlated with a high churn risk.

## Report

The final report can be found here

## Usage

To replicate the analysis, clone this GitHub repository, install the dependencies listed below, and run the following commands at the command line/terminal from the root directory of this project:

```
# download data
python data_download.py --file_path=https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv --out_type=csv  --out_file=../data/raw/IBM-Telco-Customer-Churn.csv

# run eda report
# TODO

# pre-process data 
python pre_process_script.py --input=../data/raw/IBM-Telco-Customer-Churn.csv --out_dir=../data/processed/

# create exploratory data analysis figure and write to file 
python eda_script.py --input=../data/raw/IBM-Telco-Customer-Churn.csv --out_dir=../results/

# tune and test model
python src/analysis.py --train_path="data/processed/train_df.csv" --test_path="data/processed/test_df.csv" --out_dir="results/"

# render final report
# TODO
```
## Dependancies

* Python 3.9.7 and Python packages:
    + docopt==0.6.2
    + pandas==0.24.2
    + numpy==1.21.4
    + requests==2.22.0
    + scikit-learn>=1.0
    + matplotlib>=3.2.2
    + altair==4.1.0
    + seaborn==0.8.1
    + jupyter-book==0.12.1

## References