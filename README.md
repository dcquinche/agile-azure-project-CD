[![Build Status](https://dev.azure.com/odluser243333/AgilePipelineProject/_apis/build/status%2Fdcquinche.agile-azure-project-CD?branchName=main)](https://dev.azure.com/odluser243333/AgilePipelineProject/_build/latest?definitionId=1&branchName=main)

# Overview

This project consist in building a CI/CD Pipeline. In the first part we are going to do it with Github Actions along with a Makefile, requirements and application code, and then, we are going to integrate this with Azure Pipelines using the Flask web framework.

## Project Plan

* [Spreadsheet with the project plan](https://docs.google.com/spreadsheets/d/1AZy8BwaYCT0HxbYKhldTA_-8TKOAm92wgtCDIUKcAoE/edit?usp=sharing)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/Plan/Spreadsheet.png)

* [Trello board for the project](https://trello.com/invite/b/jmY7G3FV/ATTI339b43e25439fcfcf3b77369c7da1cee2D90A971/final-project)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/Plan/Trello.png)

## Instructions

### CI: Set up azure cloud shell

1. Create the following files:
  - A Makefile to build and test the application.
  - A requirements file with the packages needed.
  - A file with some functions.
  - A file to test the functions of the previous file.

2. Generate a ssh key in the shell running the `ssh-keygen -t rsa` command. Then, go to the key using the `cat /home/odl_user/.ssh/id_rsa.pub` command, copy and paste it in github ssh keys settings. Now, you can clone the repository with the SSH key like this `git clone git@github.com:dcquinche/agile-azure-project.git` and move to it `cd agile-azure-project`.

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/1_ssh_key_shell.png)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/2_ssh_key_github.png)

3. Create a virtual environment running the `python3 -m venv ~/.myrepo` command and activate it `source ~/.myrepo/bin/activate`.

4. Inside the virtual environment, you should run the `make all` command to install all the packages needed and run the local test.

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/3_virtual_environment.png)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/4_make_all.png)

### CI: Configure github actions

5. Go to actions in the repository and create a yml file (be sure you set up a python's version available) and verify that the tests pass. You can also paste the status badge in the readme file.

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/5_github_actions.png)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CI/6_status_badge.png)


You can find all the files that corresponds to this first part in the following [repository](https://github.com/dcquinche/agile-azure-project)


### Continuos Delivery on Azure

1. Clone a new repository with the flask code application or replace the files of the one already created. Then, create a virtual environment and install all the packages needed just like we did in the 3rd and 4th step above.

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CD/1_flask_files.png)

2. Create the webapp with the following command `az webapp up -n mywebapp243439 -l westeurope --resource-group Azuredevops`. You can change the name and configurations as needed.

3. Give permissions with the `chmod +x make_predict_azure_app.sh` command and run the prediction file like this `./make_predict_azure_app.sh`.

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CD/2_webapp_and_prediction.png)

![](https://github.com/dcquinche/agile-azure-project-CD/blob/main/assets/CD/3_url_app.png)

## Demo

<TODO: Add link Screencast on YouTube>


