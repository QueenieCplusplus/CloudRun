# CloudRun
An Easy way to deploy app (alternative of GKE)

Cloud Run brings "serverless" development to containers and can be run either on your own Google Kubernetes Engine (GKE) clusters or on a fully managed PaaS solution provided by Cloud Run. You will be running the latter scenario in this lab.

![architecture](https://cdn.qwiklabs.com/Ry1hidHMw9wjyWNTvENYln0NxFFyBJQyt1bPC%2Fdp0Qc%3D)

# Core Steps

(1) create a Docker Image for App

(2) use Cloud Build to create Docker Image for App (as same as step 1)

(3) deploy/pull the container image to CloudRun

(4) update Website, and roll out new version of Website without Downtime (CI/CD)

(5) GKE

-----------

# Nodejs Web Server

from Step 0

* prework-1, clone a existing website code from Github

       git clone https://github.com/googlecodelabs/monolith-to-microservices.git
       
       cd monolith-to-microservices
       
       cd ./setup.sh
       
* prework-2, test app by starting the web server

      cd ~/monolith-to-microservices/monolith
      npm start
      
      [output]
      
      Monolith listening on port 8080!
      
      [output in UI]
      
     ![](https://raw.githubusercontent.com/QueenieCplusplus/CloudRun/main/web%20preview.png)
     
* prework-3, stop the Web server

       pressing CTRL+C in Cloud Shell.
       
# Docker 

> Dockerize App use Docker cmd line

* 1.1, in cloud shell, log in Docker

       sudo usermod -a -G docker ${USER}
       
       //If you're using a Linux-based operating system, such as Ubuntu or Debian, add your username to the docker group so that you can run Docker without using sudo.
       
       // Caution: The docker group is equivalent to the root user. See Docker's documentation for details on how this affects the security of your system.
       
       // Log out and log back in for group membership changes to take effect. If you are using a virtual machine, you may need to restart the virtual machine for membership changes to take effect.
 
* 1.2, test Docker run within output of Date

       docker run busybox date
       
* 1.3, log in the repo

       gcloud auth configure-docker
       
* 1.4, pull the docker image to repo

      docker pull gcr.io/google-samples/hello-app:1.0
      
* 1.5, tag the docker image and push it to repo

      docker tag gcr.io/google-samples/hello-app:1.0 gcr.io/PROJECT_ID/[tag name]

      docker tag gcr.io/google-samples/hello-app:1.0 gcr.io/PROJECT_ID/quickstart-image:tag1
      
      docker push gcr.io/PROJECT_ID/quickstart-image:tag1
      
* 1.6, on contrast, we pull back the app from remote to local.

      docker pull gcr.io/PROJECT_ID/quickstart-image:tag1
      
* 1.7, delete docker image in repo

     gcloud container images delete gcr.io/PROJECT_ID/quickstart-image:tag1 --force-delete-tags
     
     // in project id includes : colons symbol, then check out the doc https://cloud.google.com/container-registry/docs/overview#domain-scoped_projects
     
* 1.8, sum up doc

    https://cloud.google.com/container-registry/docs/quickstart
       
# Cloud Build

from step 3

> Dockerize App use Cloud Build

* 2.1, in cloud shell, use Cloud Build to create docker Image

        
* 2.2, push it to gcr.io (a private registry)


# Cloud Run

from step 3

> Deploy a Container

* 3.1, pull it to Cloud Run PaaS

* 3.2, mgmt the Deployment

* 3.3, setup Endpoint for App in Cloud Run

# CI/CD

from step 4


# GKE

from step 5

since the docker image is saved in the private registry, GKE can pull from it to do GKE-style deployment.

see https://github.com/QueenieCplusplus/GKE

# Ref Code

66, 10445
