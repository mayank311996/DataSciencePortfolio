# Lending Money Spark 

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
This projet presents cleaning and feature engineering of lending club data that has over 140 columns and 2 million rows using Spark and building ML models using SparkML for the same. The data can be found [here](https://www.kaggle.com/wendykan/lending-club-loan-data). 

## Motivation
Best way to utilize the lockdown period is to enhance your portfolio. The aim behind this project was to present importance of Apache Spark in real world cenario. Often, people use pandas and other libraries to do data anlysis that uses single CPU and can't scale. This is not possible in industries when you are dealing with large amount of data like in tera bites or peta bites, you need something that can scale seamlessly. 


## Technical Aspect
This project is divided into two part:
1. Getting data hosted in a personal Amazon S3 bucket. Cleaning and feature engineering of data using PySpark. 
2. Building ML models using SparkML. 
    - Used __Amazon S3 Bucket__ to download raw data and upload cleand tables and ML models. (_Simulating Real World scenario_)

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
│   |+-- 
|+-- notebooks
│   |+-- Lending_Money_Spark.ipynb
|+-- requirements.txt
|+-- LICENSE
|+-- README.md

```

## To Do
1. Add XGBoost GPU version compatible with PySpark.
2. Add DeepLearning models.

## Bug / Feature Request
If you find a bug, kindly open an issue [here](https://github.com/mayank311996/DataSciencePortfolio/issues/new) by including your search query and the expected result.

If you'd like to request a new function, feel free to do so by opening an issue [here](https://github.com/mayank311996/DataSciencePortfolio/issues/new). Please include sample queries and their corresponding results.

## Technologies Used

![](https://forthebadge.com/images/badges/made-with-python.svg)

[<img target="_blank" src="https://keras.io/img/logo.png" width=200>](https://keras.io/) [<img target="_blank" src="https://flask.palletsprojects.com/en/1.1.x/_images/flask-logo.png" width=170>](https://flask.palletsprojects.com/en/1.1.x/) [<img target="_blank" src="https://number1.co.za/wp-content/uploads/2017/10/gunicorn_logo-300x85.png" width=280>](https://gunicorn.org) [<img target="_blank" src="https://www.kindpng.com/picc/b/301/3012484.png" width=200>](https://aws.amazon.com/s3/) 

[<img target="_blank" src="https://sentry-brand.storage.googleapis.com/sentry-logo-black.png" width=270>](https://www.sentry.io/) [<img target="_blank" src="https://openjsf.org/wp-content/uploads/sites/84/2019/10/jquery-logo-vertical_large_square.png" width=100>](https://jquery.com/)
<!-->
## Team
[![Rohit Swami](https://avatars1.githubusercontent.com/u/16516296?v=3&s=144)](https://rohitswami.com/) |
-|
[Rohit Swami](https://rohitswami.com/) |)
-->
## License
[![Apache license](https://img.shields.io/badge/license-apache-blue?style=for-the-badge&logo=appveyor)](http://www.apache.org/licenses/LICENSE-2.0e)

Copyright 2020 Mayank Vadsola

## Credits
- [Lending Club Data](https://www.kaggle.com/wendykan/lending-club-loan-data) 