Project Overview

This project is a Healthcare Risk Analysis System developed using Python.
It generates a synthetic healthcare dataset for 10,000 patients and performs:

Data generation
Health risk analysis
Heart rate classification
Age group categorization
Statistical analysis
Data visualization

The project helps identify patients with high health risks based on medical parameters such as:

Blood Pressure
Sugar Level
Cholesterol
Heart Rate
Features
Generate healthcare patient dataset
Categorize heart rate status
Detect patient risk levels
Group patients by age category
Perform statistical analysis
Visualize healthcare data using charts
Create correlation heatmaps
Technologies Used
Python
Pandas
NumPy
Matplotlib
Libraries Required

Install required libraries:

pip install pandas numpy matplotlib
Dataset Information

The dataset contains 10,000 patient records.

Column Name	Description
Patient_ID	Unique patient ID
Age	Patient age
Gender	Male/Female
Blood_Pressure	Blood pressure level
Sugar_Level	Blood sugar value
Cholesterol	Cholesterol level
Heart_Rate	Heart beats per minute
HR_Status	Heart rate status
Risk_Level	Patient risk category
Age_Group	Age category
Project Workflow
1. Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

These libraries are used for:

Data analysis
Numerical operations
Visualization
2. Generate Healthcare Dataset
np.random.seed(1)

n = 10000

Creates reproducible random healthcare data.

Dataset Generation
data = pd.DataFrame({
    "Patient_ID": range(1, n+1),
    "Age": np.random.randint(20, 81, n),
    "Gender": np.random.choice(["Male", "Female"], n),
    "Blood_Pressure": np.random.randint(80, 181, n),
    "Sugar_Level": np.random.randint(70, 201, n),
    "Cholesterol": np.random.randint(150, 301, n),
    "Heart_Rate": np.random.randint(60, 121, n)
})
Data Classification
3. Heart Rate Status
Logic
Heart Rate	Status
<= 100	Normal
> 100	High
Function
def heart_rate_status(hr):
    if hr <= 100:
        return "Normal"
    else:
        return "High"

A new column HR_Status is added.

4. Risk Level Detection

A patient is considered High Risk if:

Blood Pressure > 140
Sugar Level > 160
Cholesterol > 240
Heart Rate > 100

Otherwise:

Low Risk
Function
def risk_level(row):
    if (row["Blood_Pressure"] > 140 or
        row["Sugar_Level"] > 160 or
        row["Cholesterol"] > 240 or
        row["Heart_Rate"] > 100):
        return "High"
    else:
        return "Low"
5. Age Group Categorization

Patients are divided into:

Age Range	Group
20 – 40	Young
40 – 60	Middle
60 – 80	Senior
Code
data["Age_Group"] = pd.cut(
    data["Age"],
    bins=[20,40,60,80],
    labels=["Young","Middle","Senior"]
)
Statistical Analysis
Average Values
print(data.mean(numeric_only=True))

Calculates average:

Age
Blood Pressure
Sugar Level
Cholesterol
Heart Rate
Gender Distribution
print(data["Gender"].value_counts())

Counts male and female patients.

Risk Level Count
print(data["Risk_Level"].value_counts())

Counts:

High-risk patients
Low-risk patients
Data Visualizations
1. Gender Distribution Pie Chart
data["Gender"].value_counts().plot(
    kind="pie",
    autopct='%1.1f%%'
)

Displays gender percentage distribution.

2. Age Distribution Histogram
plt.hist(data["Age"])

Shows age frequency distribution.

3. Blood Pressure vs Age Scatter Plot
plt.scatter(data["Age"], data["Blood_Pressure"])

Analyzes relationship between:

Age
Blood Pressure
4. Cholesterol Boxplot
plt.boxplot(data["Cholesterol"])

Shows cholesterol distribution and outliers.

5. Correlation Heatmap
corr = data.corr(numeric_only=True)
plt.imshow(corr)

Displays relationships among health metrics.

Sample Healthcare Visualizations
Applications

This project can be used in:

Hospitals
Healthcare analytics
Medical research
AI healthcare systems
Patient monitoring systems
Health risk prediction
Future Improvements
Add disease prediction models
Use machine learning classification
Create interactive dashboards
Add real-world healthcare datasets
Predict patient survival risk
Build web-based healthcare systems
Conclusion

This Healthcare Risk Analysis System demonstrates how Python can be used for:

Healthcare data generation
Medical analysis
Patient risk classification
Statistical reporting
Data visualization

The project provides a strong foundation for advanced healthcare analytics and AI-based medical applications.
