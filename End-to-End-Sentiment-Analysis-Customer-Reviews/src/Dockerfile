#Python Image
FROM python:3.7-slim 

#Copy files to container image
ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

#Dependencies 
RUN pip install tensorflow==2.1.0 tensorflow-datasets Flask gunicorn healthcheck google-cloud-logging

#Run the flask app
CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 SentimentGunicorn:app
