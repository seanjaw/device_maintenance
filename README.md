# Device Failure Analysis

We have the following problem:

A company has a fleet of devices transmitting daily aggregated telemetry attributes. Predictive maintenance techniques are designed to help determine the condition of in-service equipments in order to predict when maintenance should be performed. This approach promises cost savings over routine or time-based preventive maintenance, because tasks are performed only when warranted.

For more analysis and code, please check out the jupyter notebook. 

# Overview

- From the dataset, we will build a model that will determine whether a device needs maintenance utilizing Machine Learning techinuqes.
- To do this, we will apply sampling methods to an imbalanced dataset and create in-depth data exploratory analysis to understand features
- Our goal is to not only to have optimal metrics, but also minimize false negatives and false positives as much as possible




# Exploratory Data Analysis

The graph below represents the amount of devices that are checked day by day. From the visualization, we can see that as each day passes, there are fewer devices that are being checked. There is a notable drop in devices checked in the beginning. All of the data recorded is within one year from 11/02/2015 to 01/01/2015.

<img width="463" alt="Screen Shot 2019-12-05 at 12 07 10 PM" src="https://user-images.githubusercontent.com/29358337/70269729-cd2b9300-1757-11ea-9879-430ad1082054.png">

There are 7 different types of devices. Below is the visualization of how often a device fails for each class. 

<img width="533" alt="Screen Shot 2019-12-05 at 4 02 38 PM" src="https://user-images.githubusercontent.com/29358337/70284425-c95c3880-1778-11ea-85ef-c7a7e583a792.png">

Most devices that fail are not reused. However, there are certain cases where a device is actually fixed and then resused for the future. There are a total of 5 cases below. 

<img width="449" alt="Screen Shot 2019-12-29 at 4 53 14 PM" src="https://user-images.githubusercontent.com/29358337/71564850-212a4e80-2a5c-11ea-9096-a922bf78e571.png">


<img width="984" alt="Screen Shot 2019-12-05 at 12 42 34 PM" src="https://user-images.githubusercontent.com/29358337/70272249-cbb09980-175c-11ea-88bf-284b285de912.png">

<img width="992" alt="Screen Shot 2019-12-05 at 12 41 49 PM" src="https://user-images.githubusercontent.com/29358337/70272291-db2fe280-175c-11ea-9b9b-a41210e5e5cb.png">

<img width="569" alt="Screen Shot 2019-12-05 at 12 40 32 PM" src="https://user-images.githubusercontent.com/29358337/70272622-64dfb000-175d-11ea-95bc-69acaee5bb98.png">

### Summary of Attributes

- The dataset is clean, and there are no missing values. All values are integer type. There is no need to fill in values.

- The dataset is imbalanced, about 0.1% of the classes are failures. We will need to be deal with this problem by either upsampling or downsampling.

- The sparse number of distinctive values in numerous columns most likely represents categorical variables. These attributes are attribute 3, 5, 7, 9, which I will encode for modeling purposes. 

- Attribute 7 and 8 are the same, so we will drop one of the two columns.

- Attribute 2, 3, 4, 5, 7, 9 are highly skewed. We will need to apply transformations. The magnitudes differ by a wide margin. Therefore scaling needs to be done. I used min max scaler to normalize the feature from range 0 to 1 and to keep the outliers.

# Model

### Bias In Data

In our dataset, the majority of the results is not failure. We will choose to oversample because there are not enough data to train the model. We have to be careful to split the dataset first and then oversample because we do not want to duplicate observations from the train set into the test set. In addition, the observations are synthetic, which should be used for training, but are actually not the real results. If allowed, the model will overlearn and provide   

### ROC Curve

<img width="398" alt="Screen Shot 2019-12-30 at 5 49 12 PM" src="https://user-images.githubusercontent.com/29358337/71607296-f0661a00-2b2c-11ea-9937-ecded3a7975a.png">

### Learning Curve

<img width="397" alt="Screen Shot 2019-12-30 at 5 50 21 PM" src="https://user-images.githubusercontent.com/29358337/71607309-04aa1700-2b2d-11ea-86e0-5e288f4dbe82.png">

### Grid Search

<img width="689" alt="Screen Shot 2019-12-31 at 3 30 40 PM" src="https://user-images.githubusercontent.com/29358337/71636285-9fb0f880-2be2-11ea-9069-df96f5f7f571.png">

### Model Results

<img width="335" alt="Screen Shot 2019-12-31 at 3 34 50 PM" src="https://user-images.githubusercontent.com/29358337/71636322-1ea63100-2be3-11ea-959c-2881c1f5176b.png">

# Deployment

<img width="274" alt="Screen Shot 2019-12-31 at 3 32 42 PM" src="https://user-images.githubusercontent.com/29358337/71636299-d129c400-2be2-11ea-8b5b-3757f335721c.png">

# Conclusion


