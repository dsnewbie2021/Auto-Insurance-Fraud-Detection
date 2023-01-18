<!-- About The Project -->
### Username / discourseID
--------- dandi-p4Gx --------------

## About the Project
# Auto Insurance Fraud Detection

![auto insurance claims](https://blog.privy.id/wp-content/uploads/2022/11/shutterstock_720284965-1-300x173.jpg)

### Business Objective
This research goal is to build binary classifier model which are able to separate fraud transactions from non-fraud transactions. We present our conclusions based on an empirical study comparing different ML models and classification metrics.

### Business Metrics

**Precision** and **recall** should be chosen as the one of the evaluation metrics in classification models.

<p align=center>
<img src=https://miro.medium.com/max/824/1*xMl_wkMt42Hy8i84zs2WGg.png
  alt=Size Limit comment in pull request about bundle size changes
  width=500 height=300>
</p>

Precision is the rate of true positives divided by the sum of true positives and false positives. Recall is the number of true positives divided by the sum of true positives and false negatives.
A high recall indicates the model is able to classify relevant (positive) results without mislabeling them as irrelevant (negative). On the other hand, high precision indicates the model is able to returned positives predicted values is correctly positives with low irrelevant results (incorrectly positives).

Recall score with low False Negative and high False Positive Rate in AUC score should be parameter to select best model.

### Working with data

1. **Data Preparation**

<p align=center>
<img src=https://github.com/DandiMahendris/Auto-Insurance-Fraud-Detection/blob/main/pict/Preparetion%20Diagram.png
  alt=Size Limit comment in pull request about bundle size changes
  width=350 height=420>
</p>

2. **Data Preprocessing and Feature Engineering**

<p align=center>
<img src=https://github.com/DandiMahendris/Auto-Insurance-Fraud-Detection/blob/main/pict/Preprocessing%20Diagram.png
  alt=Size Limit comment in pull request about bundle size changes
  width=500 height=550>
</p>

Data separated into **predictor(X)** and **label(y)**. Numerical and categorical type of data in predictor is splitted and both missing value is handled using `SimpleImputer`

```
SimpleImputer(missing_values = np.nan,
                                strategy = median)
```

```
SimpleImputer(missing_values = np.nan,
                                strategy = 'constant',
                                fill_value = 'UNKNOWN')
```

And for categorical data using `OneHotEncoder` and `OrdinalEncoder` from sklearn package.
```
OneHotEncoder(handle_unknown = 'ignore',
                                drop = 'if_binary')
```
```
OrdinalEncoder(categories=[incident_type,witnesses,incident_severity,auto_year,
                                   umbrella_limit,bodily_injuries,number_of_vehicles_involved])
```

Next, cat and num data is concatenated to normalize the data. normalization method uses `standardscaler` from sklearn package.

This normalized data is concatenated with label(y) to be balanced using `SMOTE` and `Oversampling`. However, to capture benchmark of multiple ML models, we also use unbalanced dataset as **nonbalancing**.

3. **Data Modelling**

<p align=center>
<img src=https://github.com/DandiMahendris/Auto-Insurance-Fraud-Detection/blob/main/pict/Modelling%20Diagram.png
  alt=Size Limit comment in pull request about bundle size changes
  width=680 height=580>
</p>

### Prediction using API
1. **Data Input**

	policy_bind_date: yyyy-mm-dd, <br/>
	incident_date: yyyy-mm-dd, <br/>
	months_as_customer: int, <br/>
	age: int, <br/>
	policy_number: int, <br/>
	policy_annual_premium: int, <br/>
	insured_zip: int, <br/>
	capital_gains: int, <br/>
	capital_loss: int, <br/>
	incident_hour_of_the_day: int, <br/>
	total_claim_amount: int, <br/>
	injury_claim: int, <br/>
	property_claim: int, <br/>
	vehicle_claim: int, <br/>
	policy_deductable: str, <br/>
	umbrella_limit: str, <br/>
	number_of_vehicles_involved: str, <br/>
	bodily_injuries: str, <br/>
	witnesses: str, <br/>
	auto_year: str, <br/>
	policy_state: str, <br/>
	policy_csl: str, <br/>
	insured_sex: str, <br/>
	insured_hobbies: str, <br/>
	incident_type: str, <br/>
	collision_type: str, <br/>
	incident_severity: str, <br/>
	authorities_contacted: str, <br/>
	incident_state: str, <br/>
	incident_city: str, <br/>
	property_damage: str, <br/>
	police_report_available: str, <br/>
	auto_make: str, <br/>
	auto_model: str <br/>

#### **How To Run by API?**

First, git fetch data and cd to this code directory.
try this code below

> python .\src\api.py

### Prediction using Streamlit

#### **How To Run by Streamlit?**

> streamlit run .\src\streamlit.py