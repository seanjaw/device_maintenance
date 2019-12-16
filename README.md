# Device Failure Analysis

# Overview 
This readme covers the summary of the analysis on the device maintenance dataset. I will show the Exploratory Data Analysis, sampling, modeling, and results. The notebook can also be referenced for further insight. 

We have the following problem:

A company has a fleet of devices transmitting daily aggregated telemetry attributes. Predictive maintenance techniques are designed to help determine the condition of in-service equipments in order to predict when maintenance should be performed. This approach promises cost savings over routine or time-based preventive maintenance, because tasks are performed only when warranted.

# Exploratory Data Analysis

The Data shows that there is a big drop in number of machine maintenances as time passes by. 
<img width="463" alt="Screen Shot 2019-12-05 at 12 07 10 PM" src="https://user-images.githubusercontent.com/29358337/70269729-cd2b9300-1757-11ea-9879-430ad1082054.png">


# Attributes Summary

<img width="984" alt="Screen Shot 2019-12-05 at 12 42 34 PM" src="https://user-images.githubusercontent.com/29358337/70272249-cbb09980-175c-11ea-88bf-284b285de912.png">

<img width="992" alt="Screen Shot 2019-12-05 at 12 41 49 PM" src="https://user-images.githubusercontent.com/29358337/70272291-db2fe280-175c-11ea-9b9b-a41210e5e5cb.png">

<img width="569" alt="Screen Shot 2019-12-05 at 12 40 32 PM" src="https://user-images.githubusercontent.com/29358337/70272622-64dfb000-175d-11ea-95bc-69acaee5bb98.png">

- The dataset is clean, and there are no missing values. All values are integer type.
- The dataset is imbalanced, about 0.1% of the classes are failures. We will need to be deal with this problem by either upsample or downsample.
- The sparse number of distinctive values most likely represents a categorical variable. These attributes are attribute 3, 5, 7, 9, which I will encode for modeling. 
- Attribute 7 and 8 are the same, so we will drop one of the columns.
- Attribute 2, 3, 4, 5, 7, 9 are highly skewed. We will need to apply transformations. I therefore applied a log +1p transformation to unskew.
- The magnitudes differ by a wide margin. Therefore scaling needs to be done. I used min max scaler to normalize the feature from range 0 to 1 and keep the outliers.

# Device Classifaction Analysis

There are 7 different types of devices. Below is the visualization of how often a device fails for each class.

<img width="533" alt="Screen Shot 2019-12-05 at 4 02 38 PM" src="https://user-images.githubusercontent.com/29358337/70284425-c95c3880-1778-11ea-85ef-c7a7e583a792.png">

# Model

### Oversampling Problem

- We will choose to oversample because there are not enough data to train the model. We have to be careful to split the dataset first and then oversample because Next, we will perform a cross validation and grid search. The

- In order to avoid overfitting the model, we will create an ensemble of random forest and xgboost

### ROC Curve


# Results


# Further Analysis

# Conclusion


