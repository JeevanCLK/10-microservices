# Creating an EC2 ubuntu machine in AWS and Install Jenkins then accessing it using PublicIP:8080 , Jenkins manual installation + Infrastructure automation + Configuration Automation

### Jenkins Installation
- Run the below commands.
 
```bash
sudo apt-get update
sudo apt-get install openjdk-17-jre-headless -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```

### Configure AWS and Jenkins
 
- Open port 8080 on the security group inbound rules to allow the traffic from jenkins server
- Access the Jenkins Web UI using PublicIP:8080
- Retrieve the jenkins password from cat /var/lib/jenkins/secrets/initialAdminPassword (change file permission if access denied)
- Intall the docker on jenkins server
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo chmod 666 /var/run/docker.sock
docker --version
```

- Change the Docker sock file permission in jenkins server so that jenkins would be able to run docker commands from anywhere
```bash
sudo chmod 666 /var/run/docker.sock
```
- Add the retrieved password in Web UI and create jenkins username and password
- Goto Manage Jenkins ,inside credentials- add your github and docker credentials
- Install the neccessary plugins
- Eclipse Temurin Installer
-	Maven ( for maven install - Config File Provider )
- Maven Integration
-	Pipeline Maven Integration
-	SonarQube Scanner ( just for scanning the code  and publish it in SonarQube Server where the report will be store )
-	Docker
-	Kubernetes
-	Kubernetes CLI
-	Kubernetes credentials
-	Kubernetes Client API
- Multibrach Pipeline
- Workspacecleanup
- Docker Pipeline
- Stage view

### Create a new job , give the job name and select project as multibrach pipeline
  
- Configure the job details
- Add the github project repo url and docker credentials and then save the jobs
- Jenkins should be able to build the multibranch pipeline successfully

###  To automate the jenkins server creation and jenkins installation using Terraform
 
- Install the AWS CLI in your local machine or in you AWS EC2
```bash
https://awscli.amazonaws.com/AWSCLIV2.msi
```
- Install the Terraform in your local machine or in you AWS EC2
```bash
https://releases.hashicorp.com/terraform/1.9.5/terraform_1.9.5_windows_amd64.zip
```
- Extract the downloaded zip and add the terraform path to environmental variables 
- Verify the installation using terraform --version
- If you have vs code , you can download terraform extension

### AWS CLI Configuration on Windows

- This guide will walk you through the steps to configure AWS CLI on a Windows machine after downloading it.
- create access keys in the AWS security Credentials and make a note of your Access Key ID and Password

### Prerequisites

- Ensure you have [downloaded and installed](https://aws.amazon.com/cli/) the AWS CLI on your Windows machine.

### Step 1: Open Command Prompt or PowerShell

- Press `Win + R`, type `cmd` or `powershell`, and hit `Enter`.

### Step 2: Verify the AWS CLI Installation

Run the following command to check if the AWS CLI is installed correctly:

```bash
aws --version
aws configure
AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
Default region name [None]: ap-south-1
Default output format [None]: json
AWS s3 ls
```
### Create a new terraform provider file in vs code paste the below code

- Install the Terraform in your local machine or in you AWS EC2

```bash
provider "aws" {
  region = "ap-south-1"  # Change this to your preferred region
}

resource "aws_instance" "jenkins_server" {
  ami           = "ami-0522ab6e1ddcc7055" #give here AWS AMI ID of ubuntu or linux 
  instance_type = "t2.medium"
  key_name      = "CICD"  # Ensure this keypair exists in your AWS account
  security_groups = ["default"]  # Use the default security group or specify another

  tags = {
    Name = "Jenkins Server"
  }

  ebs_block_device {
    device_name = "/dev/xvda"
    volume_size = 30  # 30 GB storage
  }

  # User data for installing Jenkins + Docker
  user_data = <<-EOF
    #! /bin/bash
    sudo apt-get update
    sudo apt-get install openjdk-17-jre-headless -y
    sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update
    sudo apt-get install jenkins -y
    sudo apt-get update
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo 
    "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
    sudo chmod 666 /var/run/docker.sock
    docker --version
  EOF
}

output "jenkins_server_public_ip" {
  value = aws_instance.jenkins_server.public_ip
}

```
- Save the above file and run the below commands in vs code terminal
```bash
aws configure (if not done)
terraform init #initiate
terraform plan -var-file="filename.tf" # creates execution plan
terraform plan -out=filename.plan. # saves the execution form
terraform apply #applies the terradorm to create the infrastrucure as provided
terraform destroy # rollback the created infrastructure
