# Simple CI/CD Pipeline
In this section, we'll push our code to Visual Studio Team Services (VSTS) and set up a CI/CD Pipeline

## Table of Contents
- [Create New team in VSTS](#create-new-team-in-vsts)
- [Push your code to VSTS](#push-your-code-to-vsts)
- [Configure Continuous Delivery](#configure-continuous-delivery)

## Create New team in VSTS
Before we get started with CI/CD, we need to create a new team in VSTS.

1. Go to your VSTS account (example: https://__username__.visualstudio.com/_projects)
2. Click the *"New Project"* button at the top right
3. On the *"Create new Project"* screen, enter a name for the project. Select *"Git"* for version control and click *"Create"*

## Push your code to VSTS
Now that we have a Git repo, we'll push the code to that repo. VSTS has created a repo for us and since we created a repo in Visual Studio when we created our project, we just need to commit our code, add the remote to the local git repo, and push

1. In Visual Studio go to Team Explorer and select *__Changes__* in the project section. Enter a comment for the code and click "Commit All"
2. Open your Git command line / shell and navigate to the folder where the .sln file is located
3. Go back to VSTS and in the new project click on *__Code__* in the top navigation
4. Copy the two commands in the *__or push an existing repository from command line__* section. Example:
    - git remote add origin https://__username__.visualstudio.com/_git/__projectname__
    - git push -u origin --all
5. Paste / run those commands in the git command line / shell opened up in step 1
Open your git command line (Git Bash Shell / Terminal)

## Configure Continuous Delivery
Now that we have the code in VS, we can set up an automated CI/CD Pipeline to push this code to the Web Application we created [in the first part](/README.md).

1. Go to <a href="https://portal.azure.com" target="_blank">https://portal.azure.com</a> and login with the same user that you are logged into Visual Studio with.
2. Navigate to the resource group that you created in the first step. You should see your App Service and App Service plan in this resource group. __*Note:*__ *If you do not see the app Service and App Service Plan, then change the directory that you are in to the correct directory by clicking on your user at the top right and selecting the correct one.*
3. Click on the App Service that you created. Once that blade comes up, click on the __Continuous Delivery (Preview)__ tab.
4. In that blade, click the __Configure__ button.
5. In the __Configure Continuous Delivery__ blade
    - Click the __Soure Code__ tab and select the Project, repository, and branch that were created above. __*Note:*__ The repository will match the name of the project, and the branch will be "master"
    - Click the __Configure Continuous Delivery__ tab and select __ASP.NET Core__ in the dropdown and click __OK__
    - No need to change the "Test" or "Configure Deployment" tabs for now.
6. Click __OK__ in the Continuous Delivery (Preview) blade. 