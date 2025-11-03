# 🏠 Data Analysis with Python – IBM Final Project

This project was developed as the final assignment of the **Data Analysis with Python (IBM)** course.  
The goal was to analyze and predict house prices in **King County, USA**, applying a complete data science pipeline.

---

## 📊 Dataset
The dataset contains residential property sales data, including variables such as:
- `sqft_living`: house size in square feet  
- `bedrooms`, `bathrooms`, `floors`  
- `waterfront`, `view`, `condition`, `grade`  
- `price`: target variable (house sale price)

---

## 🧩 Project Steps
1. **Data Importing:** reading and inspecting the dataset using *Pandas*  
2. **Data Wrangling:** handling missing values, normalizing data, converting data types  
3. **Exploratory Data Analysis (EDA):** exploring correlations, distributions, and patterns with *Matplotlib* and *Seaborn*  
4. **Model Development:** building a *Linear Regression* model using *scikit-learn*  
5. **Model Evaluation:** calculating R² and RMSE to assess performance

---

## 🧠 Key Insights
- House size (`sqft_living`) showed the highest correlation with price.  
- Features such as condition, grade, and number of bathrooms also had strong predictive power.  
- The linear regression model achieved a solid fit for price prediction, demonstrating practical use of supervised learning techniques.

---

## ⚙️ Tech Stack
- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **scikit-learn**

---

## 📁 Files
- `House_Sales_in_King_Count_USA.ipynb`: main notebook  
- `housing.csv`: dataset (if included)  
- `results/`: visual outputs (correlation heatmaps, regression plots, etc.)

---

## 🔗 Author
Developed by **Bernardo Corral** as part of the IBM Data Analyst Professional Certificate.
