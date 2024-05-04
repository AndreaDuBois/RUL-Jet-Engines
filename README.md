# Predicting Turbofan Remaining Useful Life (RUL)
The project main theme is to develop a model to perform predictive maintenance on a jet engine. The predictive maintenance approach used here is data-driven, meaning that data collected from the operational jet engine is used to perform predictive maintenance modeling. To be specific, the project aim is to build a predictive model to estimate the Remaining Useful Life ( RUL) of a jet engine based on run-to-failure data of a fleet of similar jet engines.

This repo contains the notebooks accompanying a small series of blog posts [1] on the NASA turbofan degradation dataset [2]. The turbofan dataset consists of 4 separate challenges of increasing difficulty. The engines operate normally in the beginning but develop a fault over time. For each challenge, the engines in the train set are run to failure. The timeseries in the test set end 'sometime' before failure. The goal is to predict the Remaining Useful Life (RUL) of each turbofan engine in the test set. See the table below for a short overview of the challenges.

|Dataset	|Operating conditions |	Fault modes|	Train size (nr. of engines)	| Test size (nr. of engines)|
|--------|---|---|-----|-----|
| FD001 |	1 | 1 |	100 |	100 |
| FD002	| 6	| 1	| 260	| 259 |
| FD003	| 1	| 2	| 100	| 100 |
| FD004	| 6	| 2	| 248	| 249 |

In my analysis, I only worked on FD003 and FD004 to capture the most difficult case of each set. 

# Data
Data sets consists of multiple multivariate time series. Each time series is from a different engine – i.e., the data can be considered to be from a fleet of engines of the same type. You can find the data [https://www.kaggle.com/datasets/behrad3d/nasa-cmaps](https://data.nasa.gov/Aerospace/CMAPSS-Jet-Engine-Simulated-Data/ff5v-kuh6/about_data)

The engine is operating normally at the start of each time series, and develops a fault at some point during the series. In the training set, the fault grows in magnitude until system failure. In the test set, the time series ends some time prior to system failure.

Imbalanced class distribution is a common issue in many classification tasks. It is not unusual that the training data contains highly imbalanced positive/negative examples which however reflects the true class distribution in a general population. In predictive maintenance applications, this issue exists: the imbalance of failure events to normal operation events. This issue is due to following two major reasons. First, the failure events usually rarely occurs compared to normal operation state for an in-service asset. Second, there are too few failure events. The business cannot afford to let the asset run-to-failure, as it is at the cost of equipment damage and equipment down time.

# Methods 
The initial EDA involved exploratory data analysis, including missing value analysis and distribution analysis. Feature engineering was performed by combining some sensor data and removing irrelevant features. The regression analysis model was chosen based on the dataset’s nature and the objective of predicting a continuous variable. Other models, such as Random Forest and Neural Networks, were considered due to their complexity and the fact that this model just didn’t require it. The major conclusions of the EDA were obvious points in each unit where the moment of failure begins. 


# Statement of Business Value
The potential business value of this model includes the ability to predict engine failures, reducing downtime and maintenance costs for airlines. The model can be integrated into a digital product, such as a dashboard, that allows users to input sensor data and receive an estimate of the engine’s RUL. The business value of this work includes decreasing maintenance costs, improving safety and increasing operational efficiency. 

The model’s performance can be measured by tracking the reduction in downtime and maintenance costs. Additionally, user feedback can be collected to assess the model’s usability and value. Overall, the greatest value of this project lies in its potential to improve the aviation industry’s efficiency and safety. 




I was advised by : Polanitzer, (2020, March 24). Prediction of remaining useful life of an engine based on sensors: Building a random forest in FFA. Retrieved from https://medium.com/@polanitzer/prediction-of-remaining-useful-life-of-an-engine-based-on-sensors-building-a-random-forest-in-ffad82c8a1c6

and : Kumar, S. (2020, August 24). Remaining life estimation with Keras. Retrieved from https://towardsdatascience.com/remaining-life-estimation-with-keras-2334514f9c61
