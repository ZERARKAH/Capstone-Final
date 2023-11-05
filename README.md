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

### 2-2 Data Exploration

 <img width="313" alt="Screenshot 2023-11-05 at 2 39 23 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/48ed0ac1-133b-4f21-8a73-eecb33b7077c"> <img width="313" alt="Screenshot 2023-11-05 at 2 39 36 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/34df5471-194a-4341-9435-bdcd6a679de1"><img width="693" alt="Screenshot 2023-10-08 at 3 40 08 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/8d7a979d-ade0-48c9-ac45-511bb64a55fa"> <img width="413" alt="Screenshot 2023-11-05 at 2 35 50 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/4cb16ba3-2f1e-42ca-809d-f0062c61db15"><img width="413" alt="Screenshot 2023-11-05 at 2 39 53 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/074ec437-4be5-4599-b133-7495950e5b3f">
<img width="682" alt="Screenshot 2023-11-05 at 2 49 31 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/3be69a62-1134-417b-88c4-8ca30b60bd65">

















