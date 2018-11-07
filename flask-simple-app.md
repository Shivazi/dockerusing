https://puppet.com/docs/pipelines-for-apps/free/docker-python.html

http://containertutorials.com/docker-compose/flask-simple-app.html



Flask Application

Create a new file app.py inside web and add the following python code
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Flask Dockerized'

if __name__ == '__main__':
    app.run(debug=True,host='0.0.0.0')
```
Requirements File

Requirements file states the software required to be installed in the container. Create a file requirements.txt inside web folder
```
Flask==0.10.1
```
Dockerfile

This file is needs to create a docker image and deploy it
```
FROM ubuntu:latest
MAINTAINER Rajdeep Dua "dua_rajdeep@yahoo.com"
RUN apt-get update -y
RUN apt-get install -y python-pip python-dev build-essential
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
CMD ["app.py"]
```
Build the docker Image

Run the following command to build the docker image flask-sample-one from web directory
```
$ docker build -t flask-sample-one:latest .
```
Run the Docker Container
```
$ docker run -d -p 5000:5000 flask-sample-one
```
Run:
```
docker run 7222436013ac #(image id)
```
