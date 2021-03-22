# Starbucks-classification
Exploring how Starbucks app user data can help us target customers who are likely to complete offers.

The blog for this project can be found [here](https://timblackmore.medium.com/to-the-star-buck-s-d7c2594f1476).


# Contents
 - [Quickstart](#Quickstart) 
 - [Installation](#Installation) 
 - [How to run](#How-to-run) 
 - [Motivation](#Motivation) 
 - [Project files](#Project-files) 
 - [Project summary](#Project-summary) 
 - [Acknowledgements](#Acknowledgements) 
 
 
## Installation

The libraries used in this project are outlined in requirements.txt. They can be installed using the following command.

1. Install pipenv.
``` pip3 install pipenv```

2. Install packages in virtual environment
```pipenv install -r requirements.txt```

The main packages are scikit-learn, pandas, matplotlib and imblearn.

## How to run

To run the program locally. 
1. Open up main.ipynb and run the notebook. Be patient, some of the cells take a while to execute.

## Motivation

This project fulfils one of the requirements for the completion of the Data Science nanodegree capstone project with Udacity. 

## Project files

- *requirements.txt* - Contains the required packages to set up the development envrironment.
- *main.ipynb* - A jupyter notebook which contains the data wrangling and classifications models.
- *data/portfolio* - contains the charatertistics of the starbucks offers.
- *data/transcript*  - contains the app events and transaction details.
- *data/profile* - contains the demographic data for the customer.

## Project summary

### 1. Business understanding
The goal is to complete the Data Science project as part of the Udacity nanodegree. 

We are aiming to answer two business questions.
1. Are there differences in demographics between users who successfully complete offers, versus those who do not?
2. Can we predict whether a user will successfully complete an offer?


### 2. Data understanding
Data has been provided by Starbucks. We have data for the customers (profile.json), we have the offer charateristics (portfolio.json) and we also have the data for all the app events related to the offers (transcript.json).

The data is in json format.

The demographics data is limited. We will need to create new features to improve our ability to classify our customers. There are columns in here that will need to be dummy coded.
The portfolio data is straightforward. There are some columns in here with embedded lists which will need to be extracted. 
The transcript data is a bit tricky. We will need to wrangle this data alot to work out which transactions can be related to a successful offer.

### 3. Data preparation
We undertook a lot of data wrangling. I would invite you to view the notebook to view this specifically for each dataset.

### 4. Modelling
A random forest classfier and an adaboost classifier was chosen to classify the data. The data were split into training and testing sets and then entered a pipeline. The pipeline included a column transformer to scale the numeric data. Both models were trained using GridSearchCV. To account for the class imbalance, I used SMOTE to balance the classes.

### 5. Evaluation
The F1 score was chosen to evaluate the model as it accounts for both precision an recall. We want to reward classifying the correct response for both 1 and 0. We also used the confusion matrix to interpret the success of the models.

The resulting average F Score was 0.92 for the random forest model and 0.90 for the adaboost model.

*Random forest model confusion matrix*

![image](https://user-images.githubusercontent.com/24419429/111997953-76e09000-8b13-11eb-8f72-fbd036fbd122.png)

*Adaboost model confusion matrix*

![image](https://user-images.githubusercontent.com/24419429/111998009-819b2500-8b13-11eb-8e1e-532efb6a4622.png)


## Acknowledgements
Thanks to the mentor pages within the Udacity platform which helped me find the correct information to interpret the dataset in the correct way, as well as many stack overflow articles and the scikit-learn documentations

The following articles also helped me with some decision making.

https://towardsdatascience.com/random-forest-hyperparameters-and-how-to-fine-tune-them-17aee785ee0d
https://towardsdatascience.com/using-starbucks-app-user-data-to-predict-effective-offers-20b799f3a6d5
