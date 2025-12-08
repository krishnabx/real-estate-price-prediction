# 🏡 End-to-End ML Home Price Prediction

*A complete ML → API → Frontend workflow*

I built this as a complete end-to-end machine learning project. I started by loading and cleaning the housing dataset, handling missing values, and performing outlier detection using statistical analysis. From there, I engineered new features, explored dimensionality reduction techniques, and evaluated multiple models. I used GridSearchCV for hyperparameter tuning and applied K-Fold cross-validation to validate model stability.

Once the final model was ready, I built a Flask API that returns predictions in real time. I then created a frontend using HTML, CSS, and JavaScript that collects user inputs like square footage, bedrooms, bathrooms, and location, sends them to the API, and displays the predicted price. After connecting everything end to end, I tested the system locally and organized the project so it runs smoothly as a complete ML web application.

<p align="left">──────────────────────────────────────────────────────────────────────────────────────────────────────</p>

## 📸 Demo  
![App UI](https://github.com/krishnabx/real-estate-price-prediction/blob/main/real%20estate%20price%20prediction.png)



## 🔍 Project Overview  
This project demonstrates how to take a machine learning model **all the way into a working web app**.

The system consists of:

- 🧠 **ML Model (Scikit-Learn)** trained on housing data  
- 🐍 **Flask API** to serve predictions  
- 🌐 **Frontend (HTML/CSS/JS)** for user input  
- 🔄 **Real-time inference** (API → UI update)  

Users can enter square footage, number of bedrooms/bathrooms, and location, and instantly receive a price estimate.

---

## 🧠 Machine Learning Steps  
- Data cleaning (handling missing values, outliers)  
- Feature engineering  
- Model training using Linear Regression  
- Cross-validation and evaluation  
- Saving the trained model + columns using pickle & JSON  

---

## 🛠️ Tech Stack  
**ML:** Scikit-Learn, Pandas, NumPy , Matplotlib
**Backend:** Flask (Python)  
**Frontend:** HTML, CSS, JavaScript  
**Development:** Python, Jupyter Notebook  
**Tools:** VS Code, Git, JSON  

<p align="center">· · ·</p>
