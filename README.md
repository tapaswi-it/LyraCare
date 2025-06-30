# LyraCare: Real-Time Health Monitoring & Emergency Alerts

LyraCare is a health monitoring mobile app that connects to a smartwatch to track vital signs such as heart rate, SpO₂, and ECG. The app uses AWS services to process this data in real-time, detect critical health anomalies, and alert users and emergency contacts, aiming to reduce response time in critical medical emergencies.

## Table of Contents

- [Inspiration](#inspiration)
- [What It Does](#what-it-does)
- [How It Works](#how-it-works)
- [AWS Tools Used](#aws-tools-used)
- [Lambda Implementation](#lambda-implementation)
- [Challenges & Solutions](#challenges-solutions)
- [What's Next](#whats-next)

## Inspiration

Millions of people around the world, particularly in India, lack access to real-time health monitoring systems that can alert them in emergencies. Existing wearables only track basic health data, but there is no system in place to actively process this data and provide emergency alerts. This project aims to address that gap.

## What It Does

LyraCare connects to a smartwatch to continuously monitor the user's vital signs, including:
- Heart Rate
- SpO₂ (Blood Oxygen Levels)
- ECG (Electrocardiogram)

The app uses machine learning to detect critical anomalies in the collected data and sends real-time alerts to both the user and emergency contacts when it identifies emergency-level issues.

## How It Works

1. **Data Collection**: The app integrates with smartwatch APIs to collect health data such as heart rate and SpO₂ levels in real-time.
2. **Anomaly Detection**: The data is processed through an AWS Lambda function that runs machine learning models trained to detect health anomalies.
3. **Emergency Alert**: When a critical anomaly is detected, an alert is sent via AWS SNS to notify the user and their emergency contacts immediately.

## AWS Tools Used

- **AWS Lambda**: Used for processing the health data, running anomaly detection algorithms, and handling real-time data processing without managing servers.
- **Amazon API Gateway**: Provides the endpoint for the mobile app to send data, triggering AWS Lambda to process the information.
- **Amazon SNS**: Sends real-time push notifications to users and their emergency contacts once a health anomaly is detected.
- **Amazon DynamoDB**: Stores user data, including health metrics, anomaly history, and alert logs.
- **AWS IAM**: Manages access permissions across AWS services used in the project to ensure secure access control.

## Lambda Implementation

AWS Lambda is central to the processing of health data. It serves two main purposes:
1. **Data Processing**: Upon receiving health data from the app via API Gateway, Lambda processes the data in real time.
2. **Anomaly Detection**: Lambda runs a machine learning model to detect any critical health anomalies like a sudden drop in SpO₂ or abnormal heart rate.

Additionally, Lambda is triggered by the data submission via the API Gateway, ensuring a seamless flow of data processing.

## Challenges & Solutions

1. **Balancing Accuracy and False Positives**: The model needed to be finely tuned to avoid triggering unnecessary alerts while still catching critical anomalies. This was addressed through iterative training with diverse datasets and threshold optimization.
   
2. **Integration of Wearable Data**: Each smartwatch brand (e.g., Apple Watch, Android Wear) provides different data formats and APIs. We solved this by abstracting the data collection process to handle different smartwatch platforms uniformly.

3. **Real-time Data Processing**: The real-time nature of the app required robust processing without delays. Lambda's serverless architecture provided the scalability needed for real-time health monitoring.

## What's Next

- **Model Optimization**: Improve the accuracy of the machine learning model by training it with larger, more diverse medical datasets.
- **Broader Compatibility**: Expand the app to support more smartwatch brands and enhance cross-platform compatibility.
- **Additional Features**: Add predictive health insights, personalized recommendations, and better alert customization based on user preferences and medical conditions.

---------------------

This project is built with AWS services for scalability and reliability. The use of AWS Lambda ensures that the app can scale automatically without the need for managing server infrastructure, making it an efficient solution for real-time health monitoring.

