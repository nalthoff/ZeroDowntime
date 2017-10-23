# ZeroDowntime
Hands on Lab for Zero Downtime

## Table of Contents
* [Prerequisites](#prerequisites)
* [Deploying to Azure Web Apps](#deploying-to-azure-web-apps)
* [Simple CI/CD Pipeline](/CICD.md)

## Prerequisites
- Azure Subscription [Create a free account](https://azure.microsoft.com/en-us/free/)
- VSTS Account [Sign up](https://docs.microsoft.com/en-us/vsts/accounts/create-account-msa-or-work-student)
- Visual Studio (2017 Preferred)
- Git installed [Windows](https://git-scm.com/download/win) / [Mac](https://git-scm.com/download/mac)

## Deploying to Azure Web Apps
In this section, we'll create a web app using Visual Studio and deploy that application from your local machine to Azure directly from Visual Studio

1. Open Visual Studio
2. Click File -> New -> Project
3. Select __*.NET CORE*__ from the left side and __*ASP.NET Core Web Application*__ from the middle. At the bottom name your application whatever you like (HelloWorld, ZeroDownTime, etc). Check the checkbox next to __*Create Directory for solution*__ and for __*Create new Git Repository*__ and click __*OK*__
4. On the __*New ASP.NET Core Web Application*__ Screen, select __*Web Application (Model-View-Controller)*__ and click __*OK*__
5. In the toolbar change the startup type (next to the "play" button) from *__IIS Express__* to the name of your project. For example, if your project was named *__ZeroDowntimeApp__* that is what you would see. This will run the website as a self service website and not in IIS.
6. Click the Start / Debug button to launch the App
7. After the app comes up, make a change to the *__Views/Home/Index__* view and refresh the page to see the update you just made
8. Close the browser and go back to Visual Studio
9. In the Solution Explorer, right click on the application and click __*Publish...*__
10. On the publish screen, select "__*Microsoft Azure App Service*__". Make sure the __*Create New*__ radio button is selected and click __*Publish*__
11. Now you should see the __*Create App Service*__ window. On that screen, make sure you are signed into Visual Studio with the same account that you signed up for your Azure Account with. You can either enter custom names for *__Application Name__*, *__Resource Group__* and *__App Service Plan__*, or leave the default values.
12. Click *__Create__*. Your Resource Group, Web Application and App Service Plan are now all being created in Azure. *This will take a few minutes*.
13. Once the publish is finished, your default browser will open up with the website you just published.

### Congrats! you just deployed your web app into Azure!

Next up: [Simple CI/CD Pipeline](/CICD.md)