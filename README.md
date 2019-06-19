# Google assistant Kubernetes Deployer using CircleCI and GKE

A Dialogflow agent for deploying kubernetes clusters in GKE using voice commands

This code is based on the sample code accompanying mousetree's [blog post](https://medium.com/@admm/ci-cd-using-circleci-and-google-kubernetes-engine-gke-7ed3a5ad57e) on building a Continuous Integration and Delivery (CI/CD) pipeline using CircleCI and Google
Kubernetes Engine (GKE).

The config.yml file has been edited. It now makes an API call to CircleCI in order to start the deployment job from the build job. 
This enables integration with Dialogflow via webhook. 

## On GKE:
* Create a new cluster 
* Create a new registry
* Create a service account with premissions as Kubernetes Engine Admin and Storage Admin.

## On CircleCI:
* Select the repository to start building
* Go onto project settings > Environment variables create a GCLOUD_SERVICE_KEY and paste your GKE service account token
* Create project token and user tokens 

## On your forked repo:
* Edit the config.yml file and set up the correct Google SDK details.
* Add your circle CI user token

## On Dialogflow:
* Create a new Agent
* Create a new intent named "Deploy New"
    * Add training phrases like: "Create a new deployment" "Deploy my app"
    * Toggle enable webhook call for this intent.

* Go to fulfillment and paste url on webhook : https://circleci.com/api/v1.1/project/github/$CIRCLE_PROJECT_USERNAME/$CIRCLE_PROJECT_REPONAME?circle-token=$CIRCLETOKEN
* Save

Now you can command your digital underling to do your bidding (results may vary)
