## Overview
This project aims to build a machine learning pipeline integrating a Gradient Boosting Machine (GBM) for binary classification and a Lasso regression model for continuous prediction to evaluate delinquency and prepayment risk in mortgage loans. Implemented as a Flask-based web application, it allows users to input key mortgage-related data, generating two predictions: a classification to assess the likelihood of loan default and a regression to estimate the prepayment rate, offering a comprehensive analysis of loan risk.

## Project Structure

```bash
Mortgage-Prediction/
│
├──model/
│    └── MortgagePipelineModel.pkl                     
├── requirements.txt  
├── .env
├── logs/
├── static/
│   └── images/
│   └── css/ 
│       └── index.css    
│       └── result.css     
│
├── templates/
│   └── index.html         
│   └── results.html      
│               
├── Pipeline_Handler.py              
├── app.py           
└── README.md    

```


##  Pipeline Overview :
The pipeline is structured as follows:
- Data preprocessing is done before feeding it into the models.
- The GBM model classifies the data, filtering relevant instances.
- The filtered data is passed to the Lasso regression model to predict the prepayment rate.

##  Model Integration :
The models are integrated into a single workflow:
- The GBM model filters the dataset to identify delinquent loans.
- The Lasso regression model predicts the prepayment rate for the filtered data.
This integration ensures that predictions are made efficiently, leveraging both models for better accuracy.

## Features

- User-friendly input form for essential mortgage details including `Credit Score`, `Loan-to-Value Ratio`, `Months Since Origination`, and other further features
- Generates predictions:
  - Classification: Determines the risk level 
  - Regression: Estimates the likelihood of prepayment as a percentage
This web application provides real-time feedback on prediction process duration while featuring an easy-to-navigate and visually appealing interface.


##  Deployment via Flask :
- A **Flask web application** is used to deploy the pipeline.
- The Flask app loads the pre-trained models on startup using `joblib` and exposes a `/predict` endpoint to serve predictions.
New data is sent to this endpoint, processed through the pipeline, and predictions are returned in real-time.
The pipeline successfully integrates both classification and regression models to predict mortgage loan delinquency and prepayment rates. With deployment in a Flask app, this pipeline can make real-time predictions and provide meaningful insights.


## Tools :
- Backend: Flask with python libraries
- Frontend: HTML and css for styling
- Machine Learning libraries: Scikit-learn, Pandas, NumPy
- Deployment: Flask
- aws : as a cloud platform for feployment 

## AWS Deployment :
The Flask web application is deployed on AWS Elastic Beanstalk, ensuring scalability and ease of management. The deployment process involves creating an S3 bucket for storing static files and media, Dockerizing the Flask API for consistency across environments, and using Elastic Beanstalk to manage the application infrastructure. AWS Elastic Beanstalk automatically handles the deployment, scaling, and monitoring of the application. SSL certificates for secure communication are configured using AWS Certificate Manager (ACM), while Route 53 manages the domain.

For continuous monitoring and scaling, AWS CloudWatch is implemented, and the application can scale automatically to handle varying loads. This setup ensures the application remains resilient and performs optimally during peak usage.
deployment link : http://ec2-13-60-3-130.eu-north-1.compute.amazonaws.com:5000

## conclusion : 
Finally, users can interact with the web app interface by inputting their own feature values to make predictions. By providing the relevant loan attributes through the app, users can receive real-time predictions on whether a loan will become delinquent (via the GBM model) and the expected prepayment rate (via the Lasso regression model). This makes the app accessible for end-users to explore predictions interactively.