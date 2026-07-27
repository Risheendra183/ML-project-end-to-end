# 🔥 Fire Weather Index (FWI) Prediction App

An end-to-end Machine Learning web application that predicts the Fire Weather Index (FWI) using meteorological data from the Algerian Forest Fires dataset.

## 🌟 Features
- **Machine Learning**: Utilizes an ElasticNet CV model combined with a Standard Scaler for accurate predictions.
- **Premium UI/UX**: A modern, dark-mode web interface featuring glassmorphism design, vibrant gradients, and fully responsive CSS.
- **End-to-End Deployment**: Configured for automated CI/CD deployment using AWS CodePipeline and AWS Elastic Beanstalk.

## 🛠️ Tech Stack
- **Backend**: Python, Flask
- **Machine Learning**: Scikit-Learn, Pandas, NumPy
- **Frontend**: HTML5, Vanilla CSS3
- **Deployment**: AWS Elastic Beanstalk, AWS CodePipeline

## 🚀 Getting Started Locally

### Prerequisites
Make sure you have Python 3.8+ installed on your system.

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Risheendra183/ML-project-end-to-end.git
   cd ML-project-end-to-end/project
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```bash
   python application.py
   ```

4. **Access the Web App**
   Open your browser and navigate to `http://localhost:5000`

## ☁️ Deployment (AWS)

This project is configured to be deployed on **AWS Elastic Beanstalk** using a native Python environment.

1. The `.ebextensions/python.config` file explicitly tells AWS how to serve the Flask app (`application:application`).
2. Code changes pushed to the `main` branch are automatically built and deployed via **AWS CodePipeline**.
3. **Important Note:** Make sure your CodePipeline IAM Service Role has the `AdministratorAccess-AWSElasticBeanstalk` policy attached so it has permission to create new application versions.

## 📊 Dataset Information
The model was trained on the **Algerian Forest Fires Dataset**, utilizing features like:
- Temperature, Relative Humidity (RH), Wind Speed (Ws), and Rain
- Fine Fuel Moisture Code (FFMC)
- Duff Moisture Code (DMC)
- Initial Spread Index (ISI)

---
*Developed as an end-to-end Data Science and Machine Learning project.*
