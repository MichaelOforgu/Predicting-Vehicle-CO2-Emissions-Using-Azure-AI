# 🚗 Predicting Vehicle CO₂ Emissions Using Azure AI

## 📌 Project Overview

This project focuses on predicting **CO₂ emissions** from vehicles using a **Machine Learning model built entirely on Microsoft Azure Machine Learning Studio**. The aim is to utilize vehicle specifications to accurately forecast the amount of CO₂ emitted, supporting environmentally conscious decision-making and regulatory compliance.

The model uses a **Linear Regression algorithm** due to the continuous nature of the target variable (CO₂ emissions in grams per kilometre). The solution pipeline includes data ingestion, preprocessing, model training, evaluation, and deployment for real-time inference.

---

## 📊 Dataset Description

![Screenshot 2025-03-28 at 13 29 03](https://github.com/user-attachments/assets/bfe80b6c-a80c-42f8-a234-b1c831baa61e)

### • Source
The dataset is publicly available on [Kaggle](https://www.kaggle.com/) and was originally published by the **Government of Canada** as part of their open data initiative. It has been compiled from data collected over **7 years**.

### • Structure
- **Rows**: 7385
- **Columns**: 12

### • Features and Descriptions

| Column Name            | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| `Make`                | Vehicle manufacturer                                                        |
| `Model`               | Vehicle model name                                                          |
| `Vehicle Class`       | Vehicle category (e.g., Compact, SUV, Mid-size)                             |
| `Engine Size (L)`     | Engine size in litres                                                      |
| `Cylinders`           | Number of engine cylinders                                                  |
| `Transmission`        | Type of transmission (A=Automatic, M=Manual, AV=CVT, AS=Select Shift, etc.) |
| `Fuel Type`           | X=Regular Gasoline, Z=Premium, D=Diesel, E=Ethanol, N=Natural Gas            |
| `Fuel Consumption`    | Includes city, highway, and combined consumption in L/100km and mpg         |
| `CO2 Emissions`       | Target variable (grams per kilometre)                                       |

### • Abbreviations
- **Transmission**: A = Automatic, AM = Automated Manual, AS = Automatic Select Shift, AV = Continuously Variable, M = Manual
- **Fuel Type**: X = Regular, Z = Premium, D = Diesel, E = Ethanol (E85), N = Natural Gas

---

## 🔧 Azure ML Studio Pipeline (Training Workflow)

![Screenshot 2025-03-28 at 13 26 48](https://github.com/user-attachments/assets/7f9f6d07-e522-4746-9630-8f6a2a221fbf)

### 1. **Dataset Upload & Preview**
The dataset was uploaded to Azure ML Studio and inspected using the built-in **Data Preview** tool to verify data quality and column metadata.

### 2. **Select Columns in Dataset**
Only the most relevant features were selected for model training to avoid noise and redundancy. Columns such as `Make` and `Model` (categorical with high cardinality) may be excluded or encoded accordingly.

### 3. **Clean Missing Data**
Missing values were handled using Azure's preprocessing module. Strategies include:
- Removing rows with nulls
- Imputing numerical columns using mean or median
- Ensuring consistency of categorical data

### 4. **Normalize Data**
Numerical features such as `Engine Size`, `Fuel Consumption`, and `Cylinders` were normalized to ensure equal weighting in the linear regression model.

### 5. **Split Data**
The dataset was split into **training (70%)** and **testing (30%)** sets to evaluate model generalization and prevent overfitting.

### 6. **Select Algorithm: Linear Regression**
Linear Regression was chosen as the baseline model to predict continuous CO₂ values. It calculates a line of best fit by minimizing the error between predicted and actual values.

### 7. **Train Model**
The training module was connected to the linear regression model and the preprocessed training dataset. The model learned the relationships between vehicle features and CO₂ emissions.

### 8. **Score Model**
The model was applied to the test dataset to generate predicted CO₂ emission values.

### 9. **Evaluate Model**
Model performance was evaluated using:
- **RMSE** (Root Mean Square Error)
- **MAE** (Mean Absolute Error)
- **R²** Score (Coefficient of Determination)
These metrics provide insights into model accuracy and performance.

---

## 🚀 Azure ML Studio Inference Pipeline (Deployment Workflow)

![Screenshot 2025-03-28 at 13 27 24](https://github.com/user-attachments/assets/e2c077fe-0fb6-4bd8-8da6-6fb861c74a0c)


### 1. **Enter Data Manually**
A manual input module was used to simulate real-world data entry (e.g., for a new car).

### 2. **Preprocessing via Apply Transformation**
Same preprocessing steps (normalization, column selection) from training were reused to maintain consistency.

### 3. **Model Scoring**
The trained model was used to score new incoming data and generate predictions for CO₂ emissions.

### 4. **Execute Python Script**
A custom Python script processed and formatted the scored results, readying them for output or further analysis.

### 5. **Web Service Output**
The model was deployed as a **RESTful web service**, enabling integration with external systems or user interfaces for real-time predictions.

---

## 💡 Key Learnings

- Gained hands-on experience with **Azure Machine Learning Designer** and **drag-and-drop pipeline creation**.
- Learned how to prepare and clean data in Azure ML Studio.
- Understood the process of **normalizing and transforming features**.
- Built a complete **Linear Regression model** for predicting emissions.
- Deployed the solution as a **Web Service** for real-time usage.

---

## 🛠 Tools & Technologies

- **Azure Machine Learning Studio**
- **Azure Designer Pipeline**
- **Linear Regression**
- **Python Script Module**
- **REST API for Deployment**

---

## 📬 Contact

If you have any questions, feedback, or collaboration opportunities, feel free to reach out!
