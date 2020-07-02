# End-to-End Sentiment Analysis for Customer Reviews

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)
  * [Run](#run)
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
This project explains how to build a customer reviews sentiment analysis model using TensorFlow and deployment on Google CLoud Platform. The data can be found [here](https://www.google.com). 

_Note: Some familiarity with GCP is assumed._ 

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

## Run
> STEP 1
#### Uploading Files to Google Cloud Storage

Upload all files in `/src` directory along with [trained model](https://www.google.com) and [vocabulary](https://www.google.com) to Google Cloud Storage Bucket.

In my case bucket is located at `gs://mayank-sentimentflaskapp/`. 

> STEP 2
#### Getting Files into Current Cloud Shell

Open the Cloud Shell and type following commands.
```
ls 
gsutil ls
gsutil ls gs://mayank-sentimentflaskapp/
gsutil cp -r gs://mayank-sentimentflaskapp/ .
ls
```

> STEP 3
#### Creating Docker Container

In Cloud Shell type following commands.
```
cat .dockerignore
gcloud config get-value project 
gcloud builds submit --tag gcr.io/mayank-project/sentimentflaskapp-gke .
```

> STEP 4
#### Creating Kubernetes Engine

In Cloud Shell type following commands.
```
gcloud container clusters create flaskapp-gke \
--num-nodes 1 \
--enable-basic-auth \
--issue-client-certificate \
--zone us-west1-b \
--scopes https://www.googleapis.com/auth/logging.write
```

> STEP 5
#### Applying Both YAML Files to Running Kubernetes Cluster

In Cloud Shell type following commands.
```
ls -alrt
kubectl apply -f deployment.yaml
kubectl get deployments 
kubectl get pods 

ls -alrt
kubectl apply -f service.yaml
kubectl get services
```

> STEP 6
#### Testing Deployed App

In Cloud Shell type following commands. (see `/src/examples.txt`)
```
curl 11.111.111.111/hcheck


curl 11.111.111.111/seclassifier -d '{"text":"""Still working my way through it but definitely changes your view on investment. Wish it was available on Audible"""}' -H "Content-Type: application/json" 
```

> STEP 7
#### Scaling Deployed Kubernetes Cluster

In Cloud Shell type following commands.
```
kubectl get deployment
gcloud container clusters resize flaskapp-gke --num-nodes 2 --zone us-west1-b

kubectl autoscale deployment flaskapp-gke --max 6 --min 3 --cpu-percent 50 

kubectl get deployment
kubectl get pod 
kubectl get hpa 
```

> STEP 8 
#### Deploying on Google Cloud Cloud Run (Serverless)

In Cloud Shell type following commands.
```
gcloud config set project mayank-project

gcloud run deploy sentimentflaskapp --image gcr.io/mayank-project/sentimentflaskapp-gke --platform managed --memory 1G
```

> STEP 9 
#### Testing Deployed Serverless Cluster

In Cloud Shell type following commands. (see `/src/examples.txt`)
```
curl https://xyz.xyz.xyz.xyz/hcheck 

curl https://xyz.xyz.xyz.xyz/seclassifier -d '{"text":"""Still working my way through it but definitely changes your view on investment. Wish it was available on Audible"""}' -H "Content-Type: application/json" 
```

<!--
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
|   |+-- examples.txt
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

[<img target="_blank" src="https://prnewswire2-a.akamaihd.net/p/1893751/sp/189375100/thumbnail/entry_id/0_7ljmtw18/def_height/1920/def_width/1920/version/100012/type/1" width=200>](https://cloud.google.com/) [<img target="_blank" src="https://www.kindpng.com/picc/b/301/3012484.png" width=200>](https://aws.amazon.com/s3/) 


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