# Predictive Machine Failures


<img width="854" alt="Screenshot 2023-10-03 at 4 38 00 PM" src="https://github.com/ZERARKAH/Capstone-Final/assets/130615319/4c545aa1-263a-4664-b1a6-22a2f8384f53">


# Overview


The aim of this project is to develop a predictive model to reduce machine downtime and maintenance costs, thereby boosting production efficiency. Through data analytics, we will anticipate and prevent machine failures, enhancing reliability and operational productivity. Success will be measured by tangible improvements in machine uptime and cost efficiencies.

# 1- Business Understanding

In the rapidly evolving manufacturing landscape, machine downtimes can result in significant financial losses and disrupted supply chains. Businesses seek to minimize these unexpected downtimes by predicting potential machine failures ahead of time. Our goal, in this context, is to leverage available machine data to develop a predictive maintenance model. By analyzing various machine parameters, such as air temperature, rotational speed, and tool wear, we aim to identify patterns or signs that precede a machine failure. A successful predictive model would enable businesses to take proactive measures, ensuring that maintenance or replacements are scheduled during non-peak hours, thus minimizing disruptions and financial impacts. In essence, we aim to shift from a reactive maintenance approach to a more proactive and efficient one, optimizing operations and saving costs.

# 2- Data Understanding

Our dataset encompasses 10,000 instances across 7 features, pivotal to predicting machine failures. The average air temperature hovers around 300 K, with a process temperature approximately 10 K higher, suggesting a controlled operational environment. Rotational speeds and torque values exhibit considerable variability, essential for understanding performance thresholds. Notably, the 'Target' variable indicates that machine failures occur in 3.39% of instances, underscoring the significance of addressing class imbalance. Our visual and statistical analyses reveal no missing values, ensuring robustness in subsequent modeling stages. Correlation heatmaps further delineate relationships between features, with the aim of refining predictive accuracy.
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
**Failure Type:** Type of failure, if any  





















