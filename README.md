# Predictive Machine Failures


<img width="854" alt="Screenshot 2023-10-03 at 4 38 00 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/4c545aa1-263a-4664-b1a6-22a2f8384f53">


# Overview


The aim of this project is to develop a predictive model to reduce machine downtime and maintenance costs, thereby boosting production efficiency. Through data analytics, we will anticipate and prevent machine failures, enhancing reliability and operational productivity. Success will be measured by tangible improvements in machine uptime and cost efficiencies.

# 1- Business Understanding

In the rapidly evolving manufacturing landscape, machine downtimes can result in significant financial losses and disrupted supply chains. Businesses seek to minimize these unexpected downtimes by predicting potential machine failures ahead of time. Our goal, in this context, is to leverage available machine data to develop a predictive maintenance model. By analyzing various machine parameters, such as air temperature, rotational speed, and tool wear, we aim to identify patterns or signs that precede a machine failure. A successful predictive model would enable businesses to take proactive measures, ensuring that maintenance or replacements are scheduled during non-peak hours, thus minimizing disruptions and financial impacts. In essence, we aim to shift from a reactive maintenance approach to a more proactive and efficient one, optimizing operations and saving costs.

# 2- Data Understanding

Our dataset encompasses 10,000 data points, each representing a unique machine operation instance with 7 features. These features provide insights into various machine parameters, including air temperature, process temperature, rotational speed, torque, tool wear, and the type of product being processed. Additionally, the dataset has a binary 'machine failure' label, indicating if a machine failed for that particular instance. Preliminary analysis revealed that most features follow a normal distribution, with some showing potential correlations with machine failures. Understanding the distributions, relationships, and potential data quality issues is crucial. This ensures that our subsequent modeling phase is grounded on a solid foundation of knowledge, enabling us to make informed decisions during data preprocessing and feature engineering.

### 2-1 Data Description

The dataset contains 10,000 entries and 10 columns:

**UDI:** Unique Identifier for each record  
**Product ID:** The ID for the product  
**Type:** Type of product  
**Air temperature [K]:** Air temperature in Kelvin  
**Process temperature [K]:** Process temperature in Kelvin  
**Rotational speed [rpm]:** Rotational speed in RPM (Revolutions Per Minute)  
**Torque [Nm]:** Torque in Newton-meters  
**Tool wear [min]:** Tool wear in minutes  
**Target:** Target variable (presumably whether the machine fails or not)  
**Failure Type:** Type of failure, if any.  
1. **Air temperature [K]:** Ranges from 295.3 to 304.5 Kelvin with a mean of approximately 300.0.
2. **Process temperature [K]:** Ranges from 305.7 to 313.8 Kelvin with a mean of approximately 310.0.
3. **Rotational speed [rpm]:** Ranges from 1168 to 2886 RPM with a mean of approximately 1539.
4. **Torque [Nm]:** Ranges from 3.8 to 76.6 Nm with a mean of approximately 40.0.
5. **Tool wear [min]:** Ranges from 0 to 253 minutes with a mean of approximately 108.
6. **Target:** It's either 0 or 1, and it appears that most of the values are 0, indicating that failures are relatively rare

### 2-2 Data Exploration EDA
##### - Distribution Summary

Our data exploration entailed detailed analysis of key features, presented through insightful visuals. The target variable's bar plot uncovered a class imbalance, crucial for understanding model performance. Histograms for 'Air temperature [K]' and 'Process temperature [K]', and 'Tool wear [min]' showed well-behaved distributions, while 'Rotational speed [rpm]' and 'Torque [Nm]' indicated operational nuances. Boxplots across these features highlighted outliers and the scatter plot of tool wear versus torque, categorized by product type, illuminated the relationship between usage and mechanical stress. Lastly, the correlation heatmap revealed important feature interdependencies, particularly between temperatures, guiding our predictive modeling approach.

 <img width="313" alt="Screenshot 2023-11-05 at 2 39 23 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/48ed0ac1-133b-4f21-8a73-eecb33b7077c"> <img width="313" alt="Screenshot 2023-11-05 at 2 39 36 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/34df5471-194a-4341-9435-bdcd6a679de1"><img width="693" alt="Screenshot 2023-10-08 at 3 40 08 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/8d7a979d-ade0-48c9-ac45-511bb64a55fa"> <img width="413" alt="Screenshot 2023-11-05 at 2 35 50 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/4cb16ba3-2f1e-42ca-809d-f0062c61db15"><img width="413" alt="Screenshot 2023-11-05 at 2 39 53 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/074ec437-4be5-4599-b133-7495950e5b3f">
<img width="582" alt="Screenshot 2023-11-05 at 2 49 31 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/3be69a62-1134-417b-88c4-8ca30b60bd65">

Important Observations:

- There are no missing values in the dataset. All columns have zero missing entries.​​
- Based on the heatmap, it seems that there are no extremely strong correlations between the features.
- Addressing the class imbalance can improve the model's ability to predict the minority class (machine failures in this case) more accurately.

#### -  Analyzing new data structure
 

 Initially, the dataset presented a skewed distribution, with the majority of observations representing non-failure states. Recognizing the potential bias this could introduce in predictive modeling, we undertook an over-sampling strategy to balance the classes. This approach effectively equalized the presence of both 'failure' and 'non-failure' instances in the training data, thereby providing a more equitable learning landscape for our models.

<img width="451" alt="Screenshot 2023-11-05 at 9 21 00 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/e44efadd-90b8-4490-83eb-063985300d27">
<img width="446" alt="Screenshot 2023-11-05 at 9 22 15 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/09c715e7-dd57-42d8-933e-42fc84730e04">

<img width="452" alt="Screenshot 2023-11-05 at 9 21 49 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/8a2d97ba-bb14-49e6-9c9a-557e167bf02f"> 

- In summary, the meticulous steps taken to address class imbalance and unravel feature characteristics have set a robust foundation for constructing predictive models with enhanced accuracy and reliability. As we progress, these models are anticipated to evolve into pivotal tools in the domain of predictive maintenance, driving down downtime and fostering proactive maintenance strategies.


## 3- Data Preparation

- In the data preparation step, we encoded the categorical variables and standardized the numerical features.
- The dataset was divided into 80% training and 20% testing sets.
- The class balancing via over-sampling has been completed. Now, the shapes of the training features and targets after balancing are:

Balanced training features (X_train_balanced): 15,458 samples, 5 features
Balanced training target (y_train_balanced): 15,458 samples
This shows that the minority class samples have been duplicated to match the number of the majority class, thereby balancing the dataset for training purposes. This can help improve the model's performance on the minority class by giving more examples of the failure cases for the model to learn from.​

## 4- Model Building

- Since we have a binary classification problem—predicting whether a machine will fail (1) or not (0)—we can use various algorithms like:

1. Logistic Regression
2. Random Forest
3. Gradient Boosting
4. Support Vector Machines (SVM)

<img width="443" alt="Screenshot 2023-11-06 at 3 05 58 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/9ebc7bf0-562f-4580-8daa-33d9e7af1d0a"> <img width="443" alt="Screenshot 2023-11-06 at 3 10 22 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/81091c37-3187-4161-9028-f5e8fc6ad36c">

**For the imbalanced Dataset:**

- Logistic Regression: 96.8%   

- Random Forest: 98.5%  

- Gradient Boosting: 98.45%  
 
- SVM (Support Vector Machine): 97.2%  

The Random Forest and Gradient Boosting classifiers show the highest accuracy among the models tested. However, considering the class imbalance mentioned earlier, accuracy might not be the best metric to fully understand the performance of the models. It's possible for a model to predict "No Failure" for all instances and still achieve high accuracy due to the imbalance.

**For the balanced Dataset:**

The target variable was highly imbalanced. We used over-sampling to balance the classes in the training datase.  

- Logistic Regression Accuracy: 82.1%  
- Random Forest Accuracy: 98.35%   
- Gradient Boosting Accuracy: 93.2% 
- SVM Accuracy (Support Vector Machine): 91.25%  

<img width="643" alt="Screenshot 2023-11-06 at 3 48 26 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/2d9093b7-2e0b-421c-a945-fca5b37482a9">

## Conclusion

This visualization makes it straightforward to assess the impact of class balancing on model accuracy. The annotations provide an immediate quantitative understanding of the changes in accuracy for each model due to the balancing process. As expected, the accuracy for most models decreases slightly when the data is balanced, which is common due to the increase in false positives that comes with addressing class imbalance. However, this trade-off is often acceptable, especially in predictive maintenance scenarios, because it is typically more critical to correctly identify the minority class instances (failures) even at the cost of some false alarms. The goal is to ensure that the models do not miss potential failures, which can have significant consequences.
