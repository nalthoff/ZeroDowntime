# Advanced CI/CD with Deployment Slots
In this section will be updating the basic CI/CD Deployment to deploy to a deployment slot.

## Table of Contents

- TBD
- TBD

## Create a deployment slot
We need to create a deployment slot in the existing App Service
1. Go back to the Azure Portal and select your App Service that you created
2. In the App Service blade, click the __Deployment slots__ tab.
3. In the __Add a slot__ blade, enter "staging" for a name and click __OK__
4. Once that is done creating, you should see a new item in the deployment slots called "[sitename]-staging"
5. In your browser, navigate to the site that was created in the previous step, but add -staging before .azurewebsites.net. You should see the default Azure website that says nothing has been deployed there yet. <a name="example"/>
    - example: http://zdt220171022095900-staging.azurewebsites.net/

__*Note*__: For the remainder of this section, the origional site will be considered "production" and the new deployment slot will be considered "staging"

## Deploy to a deployment slot
Now that the deployment slot is ready, lets change the deployment script to deploy to that slot.
1. Open VSTS and go to __Build and Releases -> Releases__
2. Click on the "..." next to the release definition and select __Edit__
3. Click on __Tasks v__. You should see a single task called "Deploy Azure App Service". Click on that task. 
4. On the right side, click the checkbox for __Deploy to slot__. A new dropdown for Resource Group and Slot will be shown. Select the resource group that your App Service is located in and select __staging__ for the Slot.
5. Click the __Save__ button near the top. Enter a comment about the change you made and click __OK__.

## Make a change and check the deployment slot

Lets make a change to the code and validate it goes into the staging slot
1. Make a change to the Webpage, commit the change and push the changes to VSTS
2. Go back to VSTS and wait for the Build and the release to finish
3. Open the "production" URL  (not the staging slot URL) and validate your changes are NOT there.
4. Open the URL of the staging slot and validate the changes are there.

## Switch slots
Azure allows you to easily / quickly switch the slots.

1. Go back to the Azure Portal and navigate to your App Service
2. Click on the "Deployment Slots" tab
3. On the Deployment Slots Blade, click "Swawp"
4. Select __Staging__ for source and __production__ for destination and click __OK__
5. Go back and fresh the "production" and "staging" sites. Notice that they have swapped content!

### Congrats! You've just created a zero downtime deployment! 
