# 🏡 End-to-End ML Home Price Prediction  

Interactive Web App | ML Model | Flask API | Frontend UI

## 📸 App Demo
![App Demo](https://github.com/krishnabx/real-estate-price-prediction/blob/main/real%20estate%20price%20prediction.png)

---

## 🚀 Overview

This project is a complete **end-to-end machine learning** system that predicts home prices based on square footage, bedrooms, bathrooms, and location.

It includes:

- A clean frontend UI (HTML/CSS/JS)
- A Flask backend API
- A trained machine learning regression model
- A real-time prediction pipeline
- Fully structured project files (ready for GitHub + portfolio)

This is the kind of project that shows you can build, deploy, and integrate ML into real products — not just run models in notebooks.

---

## 🧠 Tech Stack

**Machine Learning:** Scikit-Learn, Pandas, NumPy
**Backend:** Flask (Python)
**Frontend:** HTML, CSS, JavaScript
**Model Serving:** REST API
**Tools:** VS Code, Git, JSON, Python environment

---

##📌✨ Features

- Predicts home prices instantly
✔️ Real-time API using Flask
✔️ Trained model + preprocessing pipeline
✔️ Modern UI with blurred real-estate background
✔️ Location dropdown generated dynamically from JSON
✔️ Clean separation of concerns (frontend ↔ backend ↔ model)

🗂️ Project Structure
├── client
│   ├── app.html          # Frontend UI
│   ├── app.js            # Handles API calls
│   ├── app.css           # Styling + background
│
├── server.py             # Flask backend + API routes
├── util.py               # Loads model, performs predictions
├── model.pkl             # Trained ML model
├── columns.json          # Feature metadata
├── README.md             # Project documentation
└── .gitignore

🔮 How It Works
1️⃣ User enters home details

The UI collects square footage, bedrooms, bathrooms, and location.

2️⃣ JavaScript sends request to Flask
$.post("http://127.0.0.1:5000/predict_home_price", {
  total_sqft,
  bhk,
  bath,
  location
})

3️⃣ Model predicts price

Flask loads model.pkl and computes the price using processed features.

4️⃣ UI displays final prediction

Beautiful, clean output directly visible to the user.

▶️ Run the Project Locally
1. Start backend
python server.py

2. Open frontend

Open client/app.html in your browser.

That’s it. Full ML system running locally.
