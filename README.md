# Overview
This project demonstrate how to manage and devlop a python project using CI/CD with Azure Devops

## Project Plan
* Trello plan: xxx

* Project Management Template: xxx

## Instructions

### The architectural Diagram:
![Architecture Diagram](./Images/ArrchitectDiagram.png )

### Instructions for running the Python project
#### Project cloned into Azure Cloud Shell and test
Create a GubHub Repo (https://github.com/ngotrog/devops01.git)

Add created ssh key to your GitHub: Go to Settings => SSH and GPG keys => New SSH Key

* Open Cloud shell using bash and clone project then go to project folder:

 git@github.com:ngotrog/devops01.git

or

`$ git clone  git@github.com:ngotrog/devops01.git`

`$ cd devops01`

![Architecture Diagram](./Images/CloneCode.png )

* Step testing 
python -m venv myproject
source myproject/bin/activate
Run make all to install dependency, test and lint your code using command: make all

* Testing result:
After above step you see dependencies are installed, lint rate 10/10 and tests are passed as below:
![Architecture Diagram](./Images/MakeAll.png )
#### Project running on Azure App Service
Go to your Github Account and enable Github Actions
Replace .yml file with your code to make CI when any push actions perform
Push the changes to GitHub and verify that both lint and test steps pass in your project
![Architecture Diagram](./Images/Passing of Github Action.png )

CD Azure:
Run your app using command: python app.py

* You can deploy this project direct to azure using command:
az webapp up --name trongnv-app --resource-group trongnv11-rs --runtime PYTHON:3.9 --sku B1

And see the result deploy successfully:
![Architecture Diagram](./Images/DeploySuccess_MakePredict.png )

Can go to the url and check as well:
![Architecture Diagram](./Images/WebAppSuccess.png )

Note: The app service was created before.

* Running Azure App Service from Azure Pipelines automatic deployment
![Architecture Diagram](./Images/RunPipelineSuccess.png)

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:


Run prediction against a working devloyed Azure Application using command: 
```bash
$ chmod +xr make_predict_azure_app.sh
$ ./make_predict_azure_app.sh
```
![Architecture Diagram](./Images/DeploySuccess_MakePredict.png )

* Output of streamed log files from deployed application

az webapp log tail -g trongnv11-rs --name trongnv-app

![Architecture Diagram](./Images/WebappLogs.png)

## Demo

Youtube link [Video introduction project]()