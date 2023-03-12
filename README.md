# What this does?
This repo along with https://github.com/arjunc2/k8s-manifest creates a Jenkins pipeline with GitOps to deploy code into a Kubernetes cluster. CI part is done via Jenkins and CD part via ArgoCD (GitOps).

# Jenkins installation
Ensure that your software packages are up to date on your instance by uing the following command to perform a quick software update:

[ec2-user ~]$ sudo yum update –y

#Add the Jenkins repo using the following command:

[ec2-user ~]$ sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo

#Import a key file from Jenkins-CI to enable installation from the package:

[ec2-user ~]$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

[ec2-user ~]$ sudo yum upgrade

#Install Java:

[ec2-user ~]$ sudo amazon-linux-extras install java-openjdk11 -y

#Install Jenkins:

[ec2-user ~]$ sudo yum install jenkins -y

#Enable the Jenkins service to start at boot:

[ec2-user ~]$ sudo yum install jenkins -y

#Start Jenkins as a service:

[ec2-user ~]$ sudo systemctl start jenkins

#You can check the status of the Jenkins service using the command:

[ec2-user ~]$ sudo systemctl status jenkins

#Configuring Jenkins
Jenkins is now installed and running on your EC2 instance. To configure Jenkins:

Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface:

#Unlock Jenkins screen:

As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword.

#Use the following command to display this password:

[ec2-user ~]$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword

The Jenkins installation script directs you to the Customize Jenkins page. Click Install suggested plugins.

Once the installation is complete, the Create First Admin User will open. Enter your information, and then select Save and Continue.

# Install Docker

sudo yum update -y

sudo yum -y install docker

#Start Docker:

sudo service docker start

sudo service docker status

#Access Docker commands in ec2-user user:

sudo usermod -a -G docker ec2-user

sudo chmod 666 /var/run/docker.sock

docker version

# Install Git

#Perform a quick update on your instance:

sudo yum update -y
 
#Install git in your EC2 instance

sudo yum install git -y
 
#Check git version

git version

# Jenkins plugins
Install the following plugins for the demo.

	- Amazon EC2 plugin (No need to set up Configure Cloud after)
	- Docker plugin
	- Docker Pipeline
	- GitHub Integration Plugin
	- Parameterized trigger Plugin

# ArgoCD installation
Install ArgoCD in your Kubernetes cluster following this link - https://argo-cd.readthedocs.io/en/stable/getting_started/
