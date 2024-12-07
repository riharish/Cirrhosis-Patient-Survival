# Cirrhosis-Patient-Survival

Introduction 
Cirrhosis is a progressive liver disease characterized by the gradual scarring of liver tissue due to long-term damage. It can be caused by chronic conditions such as viral hepatitis, alcohol abuse, or non-alcoholic fatty liver disease (NAFLD). As the liver becomes increasingly scarred, it loses its ability to perform vital functions, including detoxifying harmful substances, producing essential proteins, and regulating blood clotting. 

Use Cases: Predicting cirrhosis patient survival is driven by the need to improve clinical decision-making in the management of cirrhosis. Healthcare providers face challenges in assessing which patients are at high risk of mortality and which ones have a higher likelihood of recovery or survival.
By developing a predictive model based on the dataset of cirrhosis patients, we aim to achieve two key objectives:
1.	Identification of Risk Factors: Understanding which factors, such as age, sex, and specific blood test results (e.g., bilirubin, albumin, prothrombin time), have a significant impact on patient survival. This information can guide medical professionals in identifying high-risk individuals.
2.	Survival Prediction: Building a machine learning model capable of predicting a patient's survival status (survived or not survived) based on the available medical data. The model can assist in prognosis by providing predictions that complement clinical judgment.

Data Description
The Cirrhosis Patient Survival Prediction Dataset was sourced from a Mayo Clinic study conducted between 1974 and 1984, focusing on primary biliary cirrhosis (PBC) of the liver. It includes medical and demographic information about cirrhosis patients, primarily aimed at studying the factors that influence survival outcomes in individuals with cirrhosis.

Instances (Rows): Each row represents a unique patient in the dataset, providing data on various clinical measures and symptoms.
Attributes (Columns): The dataset includes 20 attributes, 13 of which are numerical and 7 categorical, detailing the patient's medical status, lab results, and treatment history. 

Target variable for predictive models
Status: The survival status of the patient: Death (D), Censored (C) and Censored due to liver transplantation (CL)
