# 🔥 Fire Weather Index (FWI) Prediction App

An end-to-end Machine Learning web application that predicts the Fire Weather Index (FWI) using meteorological data from the Algerian Forest Fires dataset.

## 🎯 Problem Statement
Forest fires pose a devastating threat to ecosystems, economies, and human life. Early detection and risk assessment are critical for effective fire management and resource allocation. The **Fire Weather Index (FWI)** is a widely used metric that estimates fire danger based on weather conditions and fuel moisture. 

This project aims to solve the problem of proactive fire risk assessment by leveraging Machine Learning to predict the FWI based on daily meteorological data (such as Temperature, Relative Humidity, Wind Speed, and Rain). By providing a fast, reliable, and accessible web interface, this tool enables early warning systems and helps authorities make data-driven decisions to prevent and mitigate forest fires.

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

This project is configured for automated CI/CD using **AWS CodePipeline** and **AWS Elastic Beanstalk**. 

### Proof of Successful Deployment
![AWS CodePipeline Success](pipeline_success.png)
*(Note: Upload the screenshot of your successful pipeline to your GitHub repo and name it `pipeline_success.png` in the root folder!)*

### Step-by-Step AWS Setup Guide

#### 1. Setup AWS Elastic Beanstalk
1. Go to the AWS Management Console and navigate to **Elastic Beanstalk**.
2. Click **Create Application**.
3. **Environment tier**: Select **Web server environment**.
4. **Platform**: Choose **Python**.
5. **Application code**: Select **Sample application** for now (CodePipeline will deploy your actual code later).
6. Click **Create environment** and wait for it to finish spinning up.

#### 2. Configure the Codebase for Elastic Beanstalk
Elastic Beanstalk needs to know how to run the Flask application. This is handled by the `.ebextensions/python.config` file:
```yaml
option_settings:
  - namespace: aws:elasticbeanstalk:container:python
    option_name: WSGIPath
    value: application:application
```
*(Note: We use the explicit list syntax here to avoid strict YAML parsing errors in AWS).*

#### 3. Setup AWS CodePipeline (CI/CD)
1. Go to **CodePipeline** in the AWS Console and click **Create pipeline**.
2. **Pipeline settings**: Give it a name and allow AWS to create a new service role.
3. **Source stage**: 
   - Select **GitHub (Version 2)**.
   - Connect to your GitHub account and select this repository and the `main` branch.
4. **Build stage**: 
   - Click **Skip build stage**. (Since this is a native Python Beanstalk deployment, AWS automatically installs `requirements.txt` on the server).
5. **Deploy stage**: 
   - Deploy provider: **AWS Elastic Beanstalk**.
   - Select the Application and Environment you created in Step 1.
6. Click **Create pipeline**.

#### 4. Fix IAM Permission Error (If encountered)
If the Deploy stage fails with `"The provided role does not have the elasticbeanstalk:CreateApplicationVersion permission"`, follow these steps:
1. Go to the **IAM Console** > **Roles**.
2. Find the CodePipeline service role (e.g., `AWSCodePipelineServiceRole-...`).
3. Click **Add permissions** > **Attach policies**.
4. Search for and attach the **`AdministratorAccess-AWSElasticBeanstalk`** policy.
5. Go back to CodePipeline and click **Release change** to retry. The deployment will now succeed!

## 📊 Dataset Information
The model was trained on the **Algerian Forest Fires Dataset**, utilizing features like:
- Temperature, Relative Humidity (RH), Wind Speed (Ws), and Rain
- Fine Fuel Moisture Code (FFMC)
- Duff Moisture Code (DMC)
- Initial Spread Index (ISI)

---
*Developed as an end-to-end Data Science and Machine Learning project.*
