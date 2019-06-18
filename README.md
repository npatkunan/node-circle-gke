# KubernetesVoiceDeployer using CI/CD with CircleCI and GKE

A Dialogflow agent for deploying kubernetes clusters in GKE using voice commands

This is the sample code accompanying mousetree's [blog post](https://medium.com/@admm/ci-cd-using-circleci-and-google-kubernetes-engine-gke-7ed3a5ad57e) on building a Continuous
Integration and Delivery (CI/CD) pipeline using CircleCI and Google
Kubernetes Engine (GKE).

The config.yml file has been edited. It now makes an API call to CircleCI in order to start the deployment job from the build job. 
This enables integration with Dialogflow via webhook. 


## On Dialogflow:
* Create a new Agent
* Create a new intent named "Deploy New"
    * Add training phrases like: "Create a new deployment" "Deploy my app"
    * Toggle énable webhook call for this intent.

* Paste url on webhook : https://circleci.com/api/v1.1/project/github/$CIRCLE_PROJECT_USERNAME/$CIRCLE_PROJECT_REPONAME?circle-token=$CIRCLETOKEN
* Save

Now you can command your digital underling to do your bidding (results may vary)
