# ZeroDowntime
Hands on Lab for Zero Downtime

## Prerequisites
- Azure Subscription [Create a free account](https://azure.microsoft.com/en-us/free/)
- VSTS Account [Sign up](https://docs.microsoft.com/en-us/vsts/accounts/create-account-msa-or-work-student)

## Create New team in VSTS
Before we get started with CI/CD, we need to create a new team in VSTS.

1. Go to your VSTS account (example: https://__username__.visualstudio.com/_projects)
2. Click the *"New Project"* button at the top right
3. On the *"Create new Project"* screen, enter a name for the project. Select *"Git"* for version control and click *"Create"*

## Deploying to Azure Web Apps
In this section, we'll create a web app using Visual Studio and deploy that application from your local machine to Azure directly from Visual Studio
1. Open Visual Studio
2. Click File -> New -> Project
3. Select *.NET CORE* from the left side and *ASP.NET Core Web Application* from the middle. At the bottom name your application whatever you like (HelloWorld, ZeroDownTime, etc). Check the checkbox next to "Create Directory for solution" and for "Create new Git Repository" and click "OK"

