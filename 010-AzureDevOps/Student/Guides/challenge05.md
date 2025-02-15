# What the Hack: DevOps 

## Challenge 5 – Azure Pipelines: Continuous Delivery
[Back](challenge04.md) - [Home](../../readme.md) - [Next](challenge06.md)

### Introduction

In DevOps after we automate our build process, we want to automate our release process, we do this with a technique called Continuous Delivery. Please take a moment to review this brief article talking about why this is important. 

1. [What is Continuous Delivery?](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-continuous-delivery)

### Challenge

In Azure DevOps we use an Azure Pipeline to release our software. In this challenge we will create an integration or QA environment and configure our pipeline to automatically deploy our application to this environment every time new code is checked in. 

1. Create a new Release Pipeline using the Azure App Service Deployment Template using the Web App for Containers (Linux) App Type.
2. To start off our deployment will only have one stage, lets call it `Integration`
3. The output of our CI Build pipeline will be the input artifact to our CD Release pipeline, add it. 
4. Enable Continuous deployment so that each time the CI pipeline finishes successfully, this pipeline will start. 
5. If you look at the tasks for our `Integration` stage you will see a single `Deploy Azure App Service` task, however before we do this, we will need to create our environment using the same Infrastructure as Code technique we used in the last challenge. In our ArmTemplates folder you will find a template called `container-webapp-template.json`. Examine this file in VS Code. What does it do? What parameters does the template expect?
   1. HINT: Use the same resource group that you used in the last challenge.
6. Add a **Azure Resource Group Deployment** task as the first step in your pipeline to execute this ARM template and configure its properties, the same way you did in the last challenge.
   1. NOTE: your webapp name needs to be globally unique, add `-integration` to the end.

### Success Criteria

1. You should now be able to manually trigger a successful release.
2. Make a small change to your code (for example: update some fo the HTML on the Index page `/Application/aspnet-core-dotnet-core/Views/Home/Index.cshtml`), it should automatically trigger a build and release.
3. View the website running in your integration environment.
   
[Back](challenge04.md) - [Home](../../readme.md) - [Next](challenge06.md)
