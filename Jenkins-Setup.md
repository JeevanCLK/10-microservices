# Create an EC2 ubuntu machine in AWS and Install Jenkins then access it using PublicIP:8080

1. **Jenkins Installation**:
- Run the below commands.
 
```bash
sudo apt-get update
sudo apt-get install openjdk-17-jre-headless -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```

- Configure AWS and Jenkins
  --
- Open port 8080 on the security group inbound rules to allow the traffic from jenkins server
- Access the Jenkins Web UI using PublicIP:8080
- Retrieve the jenkins password from cat /var/lib/jenkins/secrets/initialAdminPassword (change file permission if access denied)
- Add the retrieved password in Web UI and create jenkins username and password
- Goto Manage Jenkins ,inside credentials- add your github and docker credentials
- Install the neccessary plugins
- Eclipse Temurin Installer
-	Maven ( for maven install  Config File Provider )
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

- Create a new job , give the job name and select project as multibrach pipeline
  --
- Configure the job details
- Add the github project repo url and docker credentials and then save the jobs
- Jenkins should be able to build the multibranch pipeline successfully
  
