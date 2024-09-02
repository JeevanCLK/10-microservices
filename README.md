## An Ultimate Corporate AWS Devops Jenkins Multibranch CICD Pipeline for Deploying 10-Microservices based E-commerce application to AWS EKS: Jenkinks + ArgoCD + K8's

<div align="center">
  <div style="position: relative;">
    <img src="https://github.com/JeevanCLK/10-microservice/blob/master/devops.png" width="300" style="position: absolute; top: -500px; left: 50%; transform: translateX(-50%);" />
    <img align="right" alt="Coding" height="200" width="400" src="https://raw.githubusercontent.com/devSouvik/devSouvik/master/gif3.gif" style="position: absolute; top: -500px; right: 100;" />
  </div>
</div>

## Application Streamline and Architecture
<div align="center">
<img src="https://github.com/JeevanCLK/check/blob/master/Assets/Devops%20CIC%20Pipeline_users%2Btrans-embed.drawio.svg">
</div>

## Pipeline stages

#### CI-Cotinuous Integration using JENKINS
#### CD-Coninuous Deployment using ArgoCD
#### CM-Continuous Monitoring using Prometheus and Grafana

REQUIREMENTS from clients--->JIRA ticket raised and assigned to dev team--->DEVELOPERS writes the code and test it in local--->GITHUB Dev team pushes the code to repo---JENKINS CONTINUOUS INTEGRATION---JENKINS git Checkout--->COMPILE CODE--->TEST cases running--->AQUA-TRIVY Vulnerability scan--->SONARQUBE code quality check--->NEXUS artifactory store--->DOCKER build and tag images and push images to docker hub--->JENKINS updates image versions in manifests file in GITHUB---ARGOCD CONTINUOUS DEPLOYMENT---ARGOCD pull the docker images from dockerhub using manifests--->KUBERENETES argocd deploys the application to K8's cluster--->CONTINUOUS MONITORING using Prometheus and Grafana

## Description: 
The web-based Java Microservices based E-commerce application consist of 10 microservices,the application has been divided into microservice architecture for the high availability of the individual components to provide users a wide experience across the application usage with high availability architecture. 
## Tools Used: 
AWS IAM, AWS Linux, Git and GitHub, Jenkins, Maven, SonarQube, Nexus, Docker, Docker Hub, Argo CD, AWS EKS
<p align="left"> 
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

### Jenkins Dashboard 
<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Jenkins%20Dashboard.png">
</div>

#

### Jenkins showcasing Multibranch Pipeline jobs for the Microservices Branches

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Multibranch%20Jobs.png">
</div>

#

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Multibranch%20Jobss.png">
</div>

#


### Jenkins showcasing Successfull Buil History

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/jenkins%20Build%20History.png".png">
</div>

#

### Build docker images and tagged with DockerHub username and pushed the imgaes to DockerHub

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Docker%20Hub.png">
</div>

#

### ArgoCD showcasing the Deployment of Microservices into the pods using deployment.yml and service.ym files 
<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Argo%20CD%20dashboard1.png">
</div>

#

<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Argo%20CD%20dashboard2.png">
</div>

#

### ArgoCD showcasing the Continousouly Deployed microservices wrt service.yml files 
<div align="center">
<img src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Argocd%20Services.png">
</div>

#

### Application has been accessed with the help of DNS (Service:LoadBalancer )
<div align="center">
<img height="300" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Application%20web%20page%201.png">
</div>

#

<div align="center">
<img height="300" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Application%20web%20page%202.png">
</div>

#

<div align="center">
<img height="300" width="1000" style="margin-right: 20px" src="https://github.com/JeevanCLK/10-microservices/blob/master/Assets/Application%20web%20page%202.png">
</div>





 
