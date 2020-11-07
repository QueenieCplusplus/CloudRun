# CloudRun
An Easy way to deploy app (alternative of GKE)

Cloud Run brings "serverless" development to containers and can be run either on your own Google Kubernetes Engine (GKE) clusters or on a fully managed PaaS solution provided by Cloud Run. You will be running the latter scenario in this lab.

![architecture](https://cdn.qwiklabs.com/Ry1hidHMw9wjyWNTvENYln0NxFFyBJQyt1bPC%2Fdp0Qc%3D)

# Core Steps

(1) create a Docker Image for App

(2) deploy/pull the container image to CloudRun

(3) update Website

(4) roll out new version of Website without Downtime (CI/CD)

-----------

# Cloud Build

from Step 1

> all about Docker Image

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

* 1.1, use Cloud Build to create docker Image

        

* 1.2, pull it to gcr.io

# Cloud Run

from step 2

> Deploy a Container

* 2.1, pull it to Cloud Run PaaS

* 2.2, mgmt the Deployment

* 2.3, setup Endpoint for App in Cloud Run

# Ref Code

10445
