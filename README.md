# Udacity-AWS-MLE-ND-Project2-Build-a-ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker
The main goal of this project was to use AWS SageMaker to develop and implement an image classification model for Scones Unlimited, a logistic company that focuses on scone delivery.

# Project: 
## Deploy and Monitor a Machine Learning Workflow for Image Classification Using Amazon SageMaker
### Source: AWS Machine Learning Engineer Nanodegree Scholarship Program

## 1. Overview

This project is a part of the project assessment in the **'AWS x Udacity's Machine Learning Engineer Nanodegree Scholarship Program'**.

## 2. Getting Started

### 2.1. Project files related information:

**1. `Project2 Build-a-ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker.ipynb`:**  A machine learning working pipeline for image classification is displayed in a Jupyter notebook. This includes the necessary model training, deployment, and monitoring using Amazon SageMaker and other related AWS Services, as well as the necessary preprocessing of the scones limitless picture dataset.<br><br>
**2. `Project2_Build-a-ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker.html`:** Web-page displaying 'Project2_Build-a-ML-Workflow-For-Scones-Unlimited-On-Amazon-SageMaker.ipynb'<br><br>
**3. `Lambda.py` script:** Compilation of the 'lambda.py' scripts required by three AWS Lambda functions to build a Step Functions workflow'. (*Note: The 'lambda handler' function, normally included in the 'lambda.py' file, serves as the entry point for the Lambda function when it is triggered by an event like an HTTP request or a scheduled cron job. This function requires two objects: a "context" object that holds details about the current execution environment and a "event" object that includes details about the triggering event. The basic functionality of the Lambda function is carried out in the 'lambda handler' function, which can also interface with other AWS services, carry out calculations, and process data. The Lambda function may also provide a response to the service or client that called it.) *<br><br>
**4. `Screenshot-of-Working-Step-Function.PNG`:** screen capture of working step function. <br><br>
**5. `step-function.json`:** Step Function exported to JSON<br><br>

### 2.2. Dependencies
```
Python 3 (Data Science) - v3.7.10 kernel
ml.t3.medium instance
Python 3.8 runtime for the AWS Lambda Functions
```

## 3. Approach:

With the aid of AWS Step Functions and Lambda functions, the project seeks to create a machine learning model for picture categorization by automating a variety of machine learning activities, including data preparation, model training, deployment, and inference.

### 3.1. Individual AWS Lambda functions drafted to build an AWS Step Functions Workflow:<br>

1. The `serializeImageData` Lambda Function ([zipped `lambda_function.py` script](Lambda%20functions%20-%20python%20scripts/Lambda-1-serializeImageData-code.zip)) takes the address of an image hosted in S3, and returns a serialized JSON object.<br>
2. The `Image-Classification` Lambda Function ([zipped `lambda_function.py` script](Lambda%20functions%20-%20python%20scripts/Lambda-2-Image-Classification-code.zip)) accepts the JSON object obtained from step 1 and sends it to an endpoint, collecting inferences as a JSON object.<br>
3. The `Filter Low Confidence Inferences` Lambda Function ([zipped `lambda_function.py` script](Lambda%20functions%20-%20python%20scripts/Lambda-3-Filter-Low-Confidence-Inferences-code.zip)) takes the inference data from step 2, and filters only the images that meet the pre-defined threshold.<br>

### 3.2. Building a State Machine via AWS Step Functions

#### 3.2.1. Step Function Graph

![image](https://user-images.githubusercontent.com/62802231/218367790-1172e2d5-db7f-4efb-873b-8827be518f59.png)

#### 3.2.2. Step Function Output

![image](https://user-images.githubusercontent.com/62802231/218367919-f85e50b0-9179-4103-a9ff-111e6de23778.png)

<br>

