# Udacity DevOps Nanodegree capstone Project

The Goal of this project is to create a pipeline that automates the proccess of deploying the provided PythonApp to a kubernetes cluster on AWS

## What is built here:
- Using Jenkins to create and manage a pipeline through the provided JenkinsFile
- Using Docker to create an image of the app and push it to dockerhub
- Using AWS CloudFormation to setup the production env.
- Deploying the app.

  The pipeline has these main stages:
  - **Test**: Running unit testing on the code
  - **Build**: Dockerizing the application into an image locally
  - **Upload**: Pushing the built image to DockerHub
  - **Deploy**: Building the infrastructure and Kubernetes cluster using AWS cloudformation and deploy the Pyhthon app
  
## Getting starting:
- Install jenkins, git, python3 + pip3, docker
- Configure jenkins to create a pipeline using the provided `JenkinsFile` + configure needed credentials [DockerHub, AWS]
- Run the pipeline!
