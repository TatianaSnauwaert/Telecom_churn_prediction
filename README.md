# Telecom_churn_prediction
## Final project from Practicum by Yandex

The **goal** of this project was to develop a binary classification model that predicts whether a customer will leave the company soon based on the clientele's personal data, including information about their plans and contracts.

The ROC_AUC metric on the test set had to be no more than **0.88**.

**This project's repo includes the following files:**

- The project's jupyter notebook (Telecom_churn_prediction.ipynb);
- A pdf format of the notebook (Telecom_churn_prediction.pdf);
- Input data (final_provider folder contains: contract.csv, internet.csv, personal.csv, phone.csv);
- Project description from Practicum (final_project_description.pdf).

We have completed the following steps in this project:

**1. Descriptive statistics** 

We have merged 3 provided dataframes and studied the input.

**2. Data preprocessing**

First, we converted the target variable into a binary numeric one. Then we have converted all column names to lower case letters. We checked the data for duplicates.

Next step was to fill in missing values. It was done by filling them with the 'No' value for those cases when clients were not using the service. The missing `internet_service` values we will replace with the 'not_available' value.

Then we made some necessary changes in the data types of a few variables. Finally, we have converted all categorical variables to numeric using the OHE technique.
   
**3. EDA**

We examined both the features and the target.

There are a lot of observations with the `total_charges` values less than 100 dollars. These are most likely either new clients or those who quickly left the company after just a month. There are quite a lot of 'loyal' customers as well who stayed with the company for more than 5 years based on the days_since_join variable distribution. A big amount of clients pay around 20 dollars a month for Telecom services. Otherwise, there were no visible outliers.

We noticed that our target classes were imbalanced: there are at least twice as many observations for the customers who stayed with Telecom than for those who left. On average, there is a 26.5% probability that a customer will leave the company.

**4. Additional assignment**

We compared the monthly payment distribution (`monthly_charges`) of all active clients with the clients who have left. The biggest difference between the 2 groups is that there is a big number of active clients who pay only 20 dollars monthly for Telecom services. Exited clients used to pay more, on average. Maybe that was one of the reasons why they left the company.

Then we compared the behavior of the clients from the two above groups for both the usage of the internet services and the phone services.

The share of the internet users from the 'active' clients is 4 times smaller than that of the 'exited' users. There are more 'active' clients who are not using the internet than in the 'exited' clients group. We also see that the network is set up through a fiber optic cable for the 'exited' clients twice as many times as for the 'active' clients. This observation could mean that the quality of the fiber cable internet is lower than that of the DSL internet and that was one of the reasons for the customers to leave the company.

The phone services usage distribution is almost the same for both groups. There are slightly (3.5%) more 'active' users who are not using multiple lines than in the 'exited' group but the difference is not very significant.

    
**5. Splitting the data**

Data was split into train, validation and test sets with the 20/80 ratio.

**6. Standard scaling**

It was performed to be able to compare feature importances.

**7. Model selection**

We have compared Linear Regression, Random Forest, LightGBM and CatBoost models. We have also tuned a few hyperparameters for the Random Forest algorithm. We have chosen the LGBM model based on the ROC_AUC and Accuracy scores.

**8. Test the model**

The test score is 5.62% lower than the train score, no overfitting observed. The target metric was met.

**9. Sanity check**

The test score of our final chosen model is 45.65% higher than that of the Dummy classifier model, that we use as a baseline to analyze the model quality. It means that the modeling was useful.

**Results**

**The LGBM model** has shown the best results (**test ROC_AUC of 0.92**) in terms of quality. The target metric of 0.88 or higher has been reached.

**Logbook**

The logbook of this project can be found [here](https://docs.google.com/spreadsheets/d/1SrGdReexaSEomJGS6yR6cRwJtHA_XqpprnLaE7B6Ayg/edit#gid=124322816) (Final Project tab). Total time spent on the project: 10.5 hours with a daily average of 1.31 hours working for 8 days.
