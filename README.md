[![CircleCI](https://circleci.com/gh/akamanzi/udacity-microservice-ml-kubernetes/tree/main.svg?style=svg)](https://circleci.com/gh/akamanzi/udacity-microservice-ml-kubernetes/tree/main)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv and activate it
    *  run `python3 -m venve virtual_env_dir_name` to create the virtual environment
    *  run  `source virtual_env_dir_name/bin/activate`
* Run `make install` to install the necessary dependencies
* Run `make lint` to run linting tests on both `Dockerfile` and `app.py` or run `make all` to both install dependencies and run linting


### Running the application

1. Run the app standalone:  `python app.py`
2. Run the app in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Make predictions

  1. First ensure the app is running in one terminal using either of the above methods. 

  2. Run `./make_prediction.sh` in a separate terminal window

### Docker Steps:

* Setup and Configure Docker locally
  1. Install docker on your system. Follow this [link](https://docs.docker.com/get-docker/) instrauctions on installation
  2. Run the app in docker: `./run_docker.sh`
  3. Check if the image is created: `docker images`
  4. make pridictions: `./make_prediction.sh`
  5. uplaod docker image to docker hub: `./upload_docker.sh`

### Kubernetes Steps

* Setup and Configure Kubernetes locally
  1. Install kubernetes. If you installed docker desktop it comes with kubernetes you don't need to do another installation
  2. Install minikube. Follow instructions [here](https://minikube.sigs.k8s.io/docs/start/) for installation and setup
  3. Start minickube: `minikube start`
  4. deploy with kubernetes: `./run_kubernetes.sh ## assumes image is already uploaded to dockerhub`  
  5. make predictions: `./make_prediction.sh`

### Project files description

* `app.py`: Contains code that run the prediction model
* `Dockerfile`: Contains instructions to contenarize the app. 
* `docker_out.txt`: Contains sample output after making predictions with dockerised app
* `kubernetes_out.txt`: Contains sample output for predictions of the app deployed with kubernetes 
* `Makefile`: Defines a set of instructions to run using `make`. two of the instructions used are: `lint` and `install`
* `make_prediction.sh`: This file queries the model with some input data to make predicions
* `requirements.txt`: includes project dependencies
* `run_docker.sh`: script that runs the dockerised app
* `run_kubernetes.sh`: script that setups and runs the app with kubernetes 
* `uplaod_docker.sh`: script that uplaods local app docker image to docker hub



