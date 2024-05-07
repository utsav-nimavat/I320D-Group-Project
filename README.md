# Health Insurance Cross-Sell Prediction

### Project Goal

The project aims to utilize predictive models to determine whether existing health insurance holders will likely purchase the company’s adjacent product - vehicle insurance. Our analysis considers different customer-oriented characteristics to gauge the degree of interest of those individuals subscribing to our insurance policies. Our approach is to assist insurance companies and actuarial scientists in expanding their customer base by generating additional revenue from existing customers through cross-selling, which encourages customers to purchase different products or services to increase the spending thus enhancing customer loyalty.

### Dataset documentation

The dataset that we used for our project can be found on Kaggle [here](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction/data).

Our features are as listed below:
| Variable | Definition |
| --- | --- |
| ID | Unique ID for the customer |
| Gender | Gender of the customer |
| Age | Age of the customer |
| Driving_License | 0 : Customer does not have DL, 1 : Customer already has DL |
| Region_Code | Unique code for the region of the customer |
| Previously_Insured | 1 : Customer already has Vehicle Insurance, 0 : Customer doesn't have Vehicle Insurance |
| Vehicle_Age | Age of the Vehicle |
| Vehicle_Damage |1 : Customer got his/her vehicle damaged in the past. 0 : Customer didn't get his/her vehicle damaged in the past.|
| Annual_Premium | The amount customer needs to pay as premium in the year |
| Policy_Sales_Channel | Anonymized Code for the channel of outreaching to the customer ie. Different Agents, Over Mail, Over Phone, In Person, etc. |
| Vintage | Number of Days, Customer has been associated with the company |
| Response | 1 : Customer is interested, 0 : Customer is not interested |

### Model training & testing
**Further details are available in the Project Report. Please refer to it for a full breakdown.**

All categorical features were manually encoded, and numerical features scaled with MinMaxScaler. TomekLinks undersampling was used via the Imbalanced-Learn library to undersample the data and correct imbalanced class distributions.

The dataset was split into 70% training and 30% testing data. Only the training data was undersampled, with testing data left untouched.

Using the LazyPredict library, 3 models (RandomForest Classifier, Bagging Classifier, ExtraTrees Classifier) were picked. After K-fold cross-validation with 5 folds, ablation tests, and ROC curve plotting, ExtraTreesClassifier was picked as our model to use going forward to perform cross-sell prediction.

### Results

We discovered that our model was too afraid to predict class 1, meaning it could not accurately predict given the data. Precision and Recall for class 1 were extremely low, with more false negatives and positives than true positives. Further analysis revealed that there is a fundamental problem with the dataset that we could not discover due to time constraints. 

Further feature engineering could possibly help our model performance, but we suspect the dataset itself does not have relevant enough features to predict whether customers would be interested in health insurance.
