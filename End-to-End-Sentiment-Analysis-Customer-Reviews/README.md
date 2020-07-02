# End-to-End Sentiment Analysis for Customer Reviews

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)
  * [Directory Tree](#directory-tree)
  * [To Do](#to-do)
  * [Bug / Feature Request](#bug---feature-request)
  * [Technologies Used](#technologies-used)
  * [License](#license)
  * [Credits](#credits)

<!--
## Demo
Link: [https://indian-currency-prediction.herokuapp.com](https://indian-currency-prediction.herokuapp.com/)

[![](https://i.imgur.com/5gj4USj.png)](https://indian-currency-prediction.herokuapp.com/)
-->
## Overview
This project explains how to build a customer reviews sentiment analysis model using TensorFlow and deployment on Google CLoud Platform. The data can be found [here](https://www.kaggle.com/wendykan/lending-club-loan-data). 

## Motivation
The aim behind this project was to present end-to-end model deployement in real world cenario. It is crucial to know how we can deploy our trained model on a cloud platform like GCP that can be scalable according to real world internet traffic. 

## Technical Aspect
This project is divided into two part:
1. Getting the Amazon customer review data and building a sentiment analysis model using TensorFlow. 
2. Containerizing and deploying trained model on GCP. 
    - Used __Google Cloud Storage__ to upload trained model and Flask app.
    - Explainig use of __Cloud Shell__ for interaction with Google Cloud Platform.
    - Containerizing the model, Flask app and dependencies and uploading to __Google Cloud Container Registry__.
    - Deploying the container using __Google Cloud Kubernetes Engine__.
    - Deploying the container using __Google Cloud Cloud Run (Serverless)__.

## Installation
The Code is written in Python 3.7. If you don't have Python installed you can find it [here](https://www.python.org/downloads/). If you are using a lower version of Python you can upgrade using the pip package, ensuring you have the latest version of pip. To install the required packages and libraries, run this command in the project directory after [cloning](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) the repository:
```bash
pip install -r requirements.txt
```
<!--
## Run
> STEP 1
#### Linux and macOS User
Open `.bashrc` or `.zshrc` file and add the following credentials:
```bash
export AWS_ACCESS_KEY="your_aws_access_key"
export AWS_SECRET_KEY="your_aws_secret_key"
export ICP_BUCKET='your_aws_bucket_name'
export ICP_BUCKET_REGION='bucket_region'
export ICP_UPLOAD_DIR='bucket_path_to_save_images'
export ICP_PRED_DIR='bucket_path_to_save_predictions'
export ICP_FLASK_SECRET_KEY='anything_random_but_unique'
export SENTRY_INIT='URL_given_by_sentry'
```
Note: __SENTRY_INIT__ is optional, only if you want to catch exceptions in the app, else comment/remove the dependencies and code associated with sentry in `app/main.py`

#### Windows User
Since, I don't have a system with Windows OS, here I collected some helpful resource on adding User Environment Variables in Windows.

__Attention__: Please perform the steps given in these tutorials at your own risk. Please don't mess up with the System Variables. It can potentially damage your PC. __You should know what you're doing__. 
- https://www.tenforums.com/tutorials/121855-edit-user-system-environment-variables-windows.html
- https://www.onmsft.com/how-to/how-to-set-an-environment-variable-in-windows-10

> STEP 2

To run the app in a local machine, shoot this command in the project directory:
```bash
gunicorn wsgi:app
```

## Deployement on Heroku
Set the environment variable on Heroku as mentioned in _STEP 1_ in the __Run__ section. [[Reference](https://devcenter.heroku.com/articles/config-vars)]

![](https://i.imgur.com/TmSNhYG.png)

Our next step would be to follow the instruction given on [Heroku Documentation](https://devcenter.heroku.com/articles/getting-started-with-python) to deploy a web app.-->

## Directory Tree 
```
|+-- src 
│   |+-- SentimentFlaskapp.py
|   |+-- scratch.txt
|   |+-- SentimentGunicorn.py
|   |+-- Dockerfile
|   |+-- .dockerignore
|   |+-- deployment.yaml
|   |+-- service.yaml
|+-- notebooks
│   |+-- Sentiment-Analysis-For-Customer-Reviews.ipynb
|+-- requirements.txt
|+-- LICENSE
|+-- README.md

```

## To Do
1. Add Transformer models.
2. Deploy using Google Cloud Function.

## Bug / Feature Request
If you find a bug, kindly open an issue [here](https://github.com/mayank311996/DataSciencePortfolio/issues/new) by including your search query and the expected result.

If you'd like to request a new function, feel free to do so by opening an issue [here](https://github.com/mayank311996/DataSciencePortfolio/issues/new). Please include sample queries and their corresponding results.

## Technologies Used

![](https://forthebadge.com/images/badges/made-with-python.svg)

<!--
[<img target="_blank" src="https://en.wikipedia.org/wiki/Apache_Spark#/media/File:Apache_Spark_logo.svg" width=200>](https://spark.apache.org/docs/latest/) [<img target="_blank" src="https://www.kindpng.com/picc/b/301/3012484.png" width=200>](https://aws.amazon.com/s3/) 

[<img target="_blank" src="https://sentry-brand.storage.googleapis.com/sentry-logo-black.png" width=270>](https://www.sentry.io/) [<img target="_blank" src="https://openjsf.org/wp-content/uploads/sites/84/2019/10/jquery-logo-vertical_large_square.png" width=100>](https://jquery.com/)
-->

<!--
## Team
[![Rohit Swami](https://avatars1.githubusercontent.com/u/16516296?v=3&s=144)](https://rohitswami.com/) |
-|
[Rohit Swami](https://rohitswami.com/) |)
-->
## License
[![Apache license](https://img.shields.io/badge/license-apache-blue?style=for-the-badge&logo=appveyor)](http://www.apache.org/licenses/LICENSE-2.0e)

Copyright 2020 Mayank Vadsola

## Credits 
<!--
- [Lending Club Data](https://www.kaggle.com/wendykan/lending-club-loan-data)
-->