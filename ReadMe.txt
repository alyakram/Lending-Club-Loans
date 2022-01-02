Lending Club Loans:
Brief Introduction
LendingClub is a US peer-to-peer lending company, headquartered in San Francisco, California.[3] It was the first peer-to-peer lender to register its offerings as securities with the Securities and Exchange Commission (SEC), and to offer loan trading on a secondary market. LendingClub is the world's largest peer-to-peer lending platform.
Objective
Building a model that predicts whether the borrower can payback the loan or not, so in the future we can assess the customer and whether or not he's likely to payback his loan.
Main Strategy
Our main objective is not lending a person that is not going to payback his loan which would be a Type 1 error, Therefore we must depend on the recall score of the loans not payed category by doing methods that might reduce our accuracy but ultimately increasing our recall.
Step 1:
Exploratory Data Analysis and Feature Engineering
Getting a general idea of datatypes and null values for each column
Using Seaborn to visualize the data by plotting charts
We see that the labels are imbalanced with a ratio of 4:1 (fully_paid, charged_off) Imbalance between Fully Paid and being Charged Off can negatively affect our model that tries to have a high recall score for the Charged Off label, a poor recall score could be achieved when overfitting to the Fully Paid portion
We downsample the fully paid portion to the size of the charged off portion.
Removing outliers that may result in misleading interpretations.
Handling nan values and transforming strings to numeric data-types
Dropping columns if they won't be used in our model or be used in feature engineering.
Extracting the zip-code from the address column.
Encoding columns and getting dummy variables.
Filling na values with the mean for values that don't have a high correlation with the loan status.
Using Random Forest Regressor to predict the missing values in the mort_acc column as it is highly correlated to the loan_status.
Step 2:
Building the model
Splitting the data into train and test data 80, 20 split
Taking the test data and upsampling the fully paid portion to get a realistic summary of the metrics
Using a sequential model for our ANN model
Building the model to have  4 layers and an activation of rectified linear unit(except the last layer which is sigmoid), a Dropout of 0.2 and building it for binary classification using the Adam optimizer.
Saving the model and checking the losses for the model.
Checking the predictions.
Conclusion:
We get a well rounded classification report, and we get a recall score of 0.81 and an accuracy score of 0.80, we can further tune our model and get better recall score for charging off for example but that may affect our overall accuracy and that depends on how we want our model to perform.
 