[![CI](https://github.com/XueqingWu/individual_4_xueqing_wu/actions/workflows/cicd.yml/badge.svg)](https://github.com/XueqingWu/individual_4_xueqing_wu/actions/workflows/cicd.yml)

# Auto Scaling Flask App Using Azure As a Service
[Illness to Nutrition Web Service Link](https://illtonutri.lemonsky-d22a3d5c.westus2.azurecontainerapps.io/)

[Youtube Video](https://youtu.be/m-jwY_XYyP8)


## Purpose
The goal of this project is to build a publicly accessible auto-scaling container using Azure App Services and Flask. This is an easy way to build and deploy a scaleable web-hosted.


## Overview of the Service
This service take the input of an illness that useres give and return the nutrient they need for their body. It is a Flask web application integrated with OpenAI's LLM model, utilizing Docker for effective containerization.

Workflows:
1. User Input: Users input illness into the application.
1. Search: The application processes the inputted illness and searches for nutrients needed for this illness.
1. Output: The nutrients needed for this illness is listed.

Take Input:

<img width="610" alt="Screen Shot 2023-12-10 at 1 21 18 AM" src="https://github.com/XueqingWu/individual_4_xueqing_wu/assets/47194238/4905f2ad-0256-42fd-9650-b7006ee821d7">

Return Outputs:

<img width="573" alt="Screen Shot 2023-12-10 at 1 21 27 AM" src="https://github.com/XueqingWu/individual_4_xueqing_wu/assets/47194238/7e96f5ca-75bf-4739-9e91-fd4b78da4c4a">


## Key Components
1. Flask Web Application:
    - Functionality: The web app allows users to input prompts, which are then processed by the GPT-3.5 model to generate responses. The responses are displayed on a results page.
        - The web app (main.py) incorporates routes for the index page and the result page. User can input illness.
        - HTML Templates: The project contains HTML templates (index.html and result.html) providing a user-friendly interface.
1. Open AI LLM Model Integration:
    - API Interaction: The application interfaces with the Open AI LLM Model via API calls. It sends a the user input of nutrients to get predictions.
1. Docker Containerization: Dockerfile: 
    - This Dockerfile containerizes a Flask app, setting up a Docker container with Python and Gunicorn to run the web application. It encapsulates the app's code and dependencies, simplifying deployment across different environments.

## Azure Container Apps Deployment
Azure has its own docker. The web service is deployed on Azure

- Azure Container Registry:

<img width="1184" alt="Azure Container Registry" src="https://github.com/XueqingWu/individual_4_xueqing_wu/assets/47194238/f16b04b9-b635-45bc-bf06-9465253278f0">

- Azure Container Apps Deployment:

<img width="1380" alt="Azure Container Apps Deployment" src="https://github.com/XueqingWu/individual_4_xueqing_wu/assets/47194238/f140f511-c3c1-40e6-9277-29c711c4e768">

- Azure Docker Image:

<img width="1417" alt="Docker Image" src="https://github.com/XueqingWu/individual_4_xueqing_wu/assets/47194238/d676ea3e-b378-4c59-a93d-db6eca31b769">


## Preparation
1. git clone the repo
1. install: `make install`
1. get access to user token via GPT
1. create an env file and add user token
1. run: `python main.py` and navigate to the locally hosted website
1. upload image or use default image
1. build docker image: `docker build --tag <insert image name>` .
1. login to azure cli: `az login`
1. deploy azuer web app: `az containerapp up --resource-group <insert resource group> --name <insert app name> --ingress external --target-port 50505 --source` .
1. view app via `conatiner apps` and docker image via `container regsitry` in azure web portal

## Check Format and Test Errors:
1. Format code `make format`
1. Lint code `make lint`
1. Test coce `make test`


## References
1. https://github.com/nogibjj/python-ruff-template
1. https://learn.microsoft.com/en-us/azure/developer/python/tutorial-containerize-simple-web-app?tabs=web-app-flask
1. https://learn.microsoft.com/en-us/azure/container-apps/scale-app?pivots=azure-cli
1. https://github.com/Azure-Samples/msdocs-python-flask-webapp-quickstart




