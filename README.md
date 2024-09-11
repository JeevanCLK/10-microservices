<div align="center">
  <h2>E-Commerce Cloud Hosted Webapp</h2>
</div>


## An Ultimate Corporate AWS Devops Jenkins Multibranch CI Pipeline with CD pipeline using GitOps Controller ArgoCD for Deploying 11-Microservices based E-commerce application to AWS EKS : CI-Jenkinks + CD-ArgoCD => CICD - K8's

<div align="center">
  <div style="position: relative;">
    <img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/devops.png" width="350" style="position: absolute; top: -500px; left: 50%; transform: translateX(-50%);" />
    <img height="200" width="400" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Systems.png" style="position: absolute; top: -500px; right: 100;" />
  </div>
</div>

## Application Streamline and Architecture
<div align="center">
<img src="https://github.com/JeevanCLK/check/blob/master/Assets/Devops%20CIC%20Pipeline_users%2Btrans-embed.drawio.svg">
</div>

#

![Continuous Integration](https://github.com/GoogleCloudPlatform/microservices-demo/workflows/Continuous%20Integration%20-%20Main/Release/badge.svg)
Find **Protocol Buffers Descriptions** at the [`./protos` directory](/protos).

**Online Boutique** is a cloud-first microservices demo application.
Online Boutique consists of an 11-tier microservices application. The application is a
web-based e-commerce app where users can browse items,
add them to the cart, and purchase them.

Google uses this application to demonstrate the use of technologies like
Kubernetes, GKE, Istio, Stackdriver, and gRPC. This application
works on any Kubernetes cluster, like Google
Kubernetes Engine (GKE). It’s **easy to deploy with little to no configuration**.

If you’re using this demo, please **★Star** this repository to show your interest!

| Service                                              | Language      | Description                                                                                                                       |
| ---------------------------------------------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [frontend](https://github.com/JeevanCLK/10-microservices/tree/frontendservice)                           | Go            | Exposes an HTTP server to serve the website. Does not require signup/login and generates session IDs for all users automatically. |
| [cartservice](https://github.com/JeevanCLK/10-microservices/tree/cartservice)                     | C#            | Stores the items in the user's shopping cart in Redis and retrieves it.                                                           |
| [productcatalogservice](https://github.com/JeevanCLK/10-microservices/tree/productcatalogueservice) | Go            | Provides the list of products from a JSON file and ability to search products and get individual products.                        |
| [currencyservice](https://github.com/JeevanCLK/10-microservices/tree/currencyservice)             | Node.js       | Converts one money amount to another currency. Uses real values fetched from European Central Bank. It's the highest QPS service. |
| [paymentservice](https://github.com/JeevanCLK/10-microservices/tree/paymentservice)               | Node.js       | Charges the given credit card info (mock) with the given amount and returns a transaction ID.                                     |
| [shippingservice](https://github.com/JeevanCLK/10-microservices/tree/shippingservice)             | Go            | Gives shipping cost estimates based on the shopping cart. Ships items to the given address (mock)                                 |
| [emailservice](https://github.com/JeevanCLK/10-microservices/tree/emailservice)                   | Python        | Sends users an order confirmation email (mock).                                                                                   |
| [checkoutservice](https://github.com/JeevanCLK/10-microservices/tree/checkoutservice)             | Go            | Retrieves user cart, prepares order and orchestrates the payment, shipping and the email notification.                            |
| [recommendationservice](https://github.com/JeevanCLK/10-microservices/tree/recomandationservice) | Python        | Recommends other products based on what's given in the cart.                                                                      |
| [adservice](https://github.com/JeevanCLK/10-microservices/tree/adservice/src)                         | Java          | Provides text ads based on given context words.                                                                                   |
| [loadgenerator](https://github.com/JeevanCLK/10-microservices/tree/loadgeneratorservice)                 | Python/Locust | Continuously sends requests imitating realistic user shopping flows to the frontend.                                              |


## Pipeline stages

#### CI-Cotinuous Integration using JENKINS
#### CD-Coninuous Deployment using ArgoCD
#### CM-Continuous Monitoring using Prometheus and Grafana

REQUIREMENTS from clients--->JIRA ticket raised and assigned to dev team--->DEVELOPERS writes the code and test it in local--->GITHUB Dev team pushes the code to repo---JENKINS CONTINUOUS INTEGRATION---JENKINS git Checkout--->COMPILE CODE--->TEST cases running--->AQUA-TRIVY Vulnerability scan--->SONARQUBE code quality check--->NEXUS artifactory store--->DOCKER build and tag images and push images to docker hub--->JENKINS updates image versions in manifests file in GITHUB---ARGOCD CONTINUOUS DEPLOYMENT---ARGOCD pull the docker images from dockerhub using manifests--->KUBERENETES argocd deploys the application to K8's cluster--->CONTINUOUS MONITORING using Prometheus and Grafana

## Description: 
The web-based Java Microservices based E-commerce application consist of 11 microservices,the application has been divided into microservice architecture for the high availability of the individual components to provide users a wide experience across the application usage with high availability architecture. 
## Tools Used: 
AWS IAM, AWS Linux, Git and GitHub, Jenkins, Maven, SonarQube, Nexus, Docker, Docker Hub, Argo CD, AWS EKS
<p align="center"> 
<a href="https://aws.amazon.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/> </a> 
<a href="https://www.gnu.org/software/bash/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/> </a> 
<a href="https://www.linux.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a> 
<a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a> 
<a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/github/github-tile.svg" alt="github" width="40" height="40"/> </a> 
 <a href="https://www.java.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/> </a> 
<a href="https://www.vectorlogo.zone/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/apache_maven/apache_maven-ar21.svg" alt="maven" width="40" height="40"/> </a> 
<a href="https://spring.io/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" alt="spring" width="40" height="40"/> </a> 
<a href="https://www.jenkins.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/jenkins/jenkins-icon.svg" alt="jenkins" width="40" height="40"/> </a> 
<a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a> 
<a href="https://www.vectorlogo.zone/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/argoprojio/argoprojio-ar21.svg" alt="argo" width="90" height="40"/> </a> 
<a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40"/> </a> 
<a href="https://www.nginx.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nginx/nginx-original.svg" alt="nginx" width="40" height="40"/> </a> 
<a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> 
<a href="https://www.vectorlogo.zone/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/prometheusio/prometheusio-ar21.svg" alt="prometheus" width="90" height="40"/> </a>
<a href="https://grafana.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/grafana/grafana-icon.svg" alt="grafana" width="40" height="40"/> </a> 
</p>

## Application Streamline: 
Made some changes to the application using Git and committed the changes to the GitHub repository, the repo was configured with webhook applied against Jenkins URL to trigger a Jenkins job, whenever the changes were detected in the source code with the help of webhook  Jenkins start pulling the code form the GitHub repo to start the pipeline as part of continuous integration and continuous deployment ,the Jenkins declarative pipeline has  integrated with series of steps using the respective plugins for the steps to achieve CICD .

## Series of Steps Involved  
##### Step 1: Created AWS EC2 3 ubuntu machines for Jenkins, SonarQube and for Nexus repo 
##### Step 2: Installed and configured Jenkins, SonarQube container and Nexus Container on their respective servers.
##### Step 3: Installed and configured the docker on all three servers and created an Docker Hub account to store docker images.
##### Step 4: Created an AWS EKS cluster with 2 nodes and configured the necessary policies
##### Step 5: Configured Git and made some changes to the code and then pushed the code to the GitHub Repo
##### Step 6: GitHub repo was configured with webhook of Jenkins URL to trigger a Jenkins job whenever changes detected in repo
##### Step 7: Configured the Jenkins global tools configuration with all the necessary downloaded plugins for the streamline            
##### Step 8: Configured the Jenkins credentials to securely store the GitHub token, User ID’s and Passwords of SonarQube server,Nexus server and Docker Hub credentials  to use it in pipeline as Env Variables .
##### Step 9: Write the Jenkins pipelines for all the microservices with series of steps as a part of CI which is checked into root directory of the each microservices source code
##### Step 10: Write the docker files for the each microservices and checked them into their respective microservices source code directory
##### Step 11: Jenkins pipeline start building the project using the Jenkins file consist of below series of steps
##### Step 12: Jenkins to update image versions in manifests files present in the github repo
##### Step 13: Installed and configured Argo CD on AWS EKS cluster for the continuous integration and continuous deployment
##### Step 14: Created docker secrets in the AWS EKS cluster to store the Docker Hub User ID and Password to pull the images from Hub.
##### Step 15: Created Repo and added the project URL in ARGO CD and Created an application to start deploying the application to AWS EKS
##### Step 16: ArgoCD will start pulling the images from DockerHub using the manifest files based on the images pull policy set creteria and it wil deploy the application to the AWS EKS cluster,then configure the K8's service load balancer to expose the application to internet.

#

### Github Project Repo Showcasing 11-Microservices for Continuous Integration by Jenkins

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Github%20Microservices%20Repo.png">
</div>

#

### Jenkins Dashboard : showcasing Multibranch Pipeline jobs for the Microservices Branches

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Jenkins%20Multibranch%20pipeline%20Dashboard.png">
</div>

#

### Jenkins showcasing Successfull Build History

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/jenkins%20Build%20History.png".png">
</div>

#

### Built docker images and tagged with DockerHub username and pushed the imgaes to DockerHub

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/DockerHub.png">
</div>

#

### Github Project Repo Showcasing Service.yml and Deployment.yml files for Continuous Deployment by ArgoCD

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Github%20Repo%20Services%2BDeployment%20yml%20files.png">
</div>

#

### ArgoCD Dashboard showcasing the Deployment of Microservices 

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/AroCD%20Dashboard.png">
</div>

#

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/argocd%20application%20deployment%201.png">
</div>

#

#

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/argocd%20application%202deployment.png">
</div>

#

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/argocd%20application%20deployment%203.png">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/argocd%20application%20deployment%204.png">
</div>

#

### ArgoCD showcasing endpoints
<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/argocd%20endpoints.png">
</div>

#

### ArgoCD showcasing pods distribution amoung 2 nodes
<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Pod%20Distribution%20to%20Nodes.png">
</div>

#

### Kubernetes Cluster in AWS cloud shell

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/K8's%20cluster%20in%20cloud%20shell.png">
</div>

#

### Application has been accessed with the help of DNS (Frontend-Service:LoadBalancer )


<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Online%20Boutique.png">
</div>

#

<div align="center">
<img height="300" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Application%20Dashboard.png">
</div>


#

<div align="center">
<img height="450" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/K8's%20cluster%20in%20cloud%20shell.png">
</div>

#

<div align="center">
<img height="450" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Shipping%20address.png">
</div>

<div align="center">
  <h1>🛍👜👟👞👗👕👠That's It . Happy Shopping👢👜🛒🕶😎🛍👜🤝</h1>
</div>

 
