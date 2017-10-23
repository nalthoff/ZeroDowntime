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

Azure is now setting up a pre-configured CI/CD Pipeline that will be kicked off when new code is pushed to the repo

## Check out the new CI/CD Pipeline

Lets go take a look at the build / release that was set up
1. In VSTS, navigate to your project and click on __Build and Release --> Builds__. You should see a build with an auto generated name. Click on the build to see the details. 
    - Click "Edit" near the top right to view the steps that were created. For a ASP.NET Core app, Azure will create the standard Restore/Build/Test/Publish steps.
2. Click on __Releases__ in the sub navigation. You should see a release definition with an auto generated name. Click on the "..." next to the release definition and click __Edit__ to view the release.
    - Azure will automatically create a build with a single Environment and with a single task that deploys the website.

## Push new changes to VSTS

Now that we've got the CI/CD Build pipeline configured, we'll change some code and push the changes to VSTS, which should kick off a build
1. Go back to Visual Studio and make a change to the __Views/Home/Index__ view
2. Go to __Team Explorer__, Switch to __Changes__, add a comment and commit the code change.
3. Click __Sync__ and __push__. You can push your code via Git shell if you prefer as well.
4. Go back to VSTS and select __Build and Release -> Builds__. You should see that the build has a status of "in progress". It will take a few minutes for that to complete.
5. Once that completes, go to the __releases__ tab. You should see a new release that is in process. That release is pushing the code to your app Service created in the first step.

