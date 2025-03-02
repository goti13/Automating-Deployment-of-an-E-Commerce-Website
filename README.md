# Automating-Deployment-of-an-E-Commerce-Website
Capstone Project: Cl/ CD Mastery

**Project Scenerio**

A technology consulting firm, is adopting a cloud architecture for its software applications. As a DevOps Engineer, your task is to design and implement a robust CI/CD pipeline using Jenkins to automate the deployment of a web apolication. 
The goal is to achieve continuous intearation, continuous deployment and ensure the scalability and reliability of the applications.

**Prerequisite**

- Knowledge of Jenkins essentials
- Completion of Introduction to Jenkins, Jenkins Freestyle Project, and Jenkins Pipeline Job mini projects.


# Project Components

1. Jenkins Server Setup

**Objective: Configure Jenkins server for Cl/CD pipeline automation**

Steps:

i. Install Jenkins on a dedicated server.

ii. Set up necessary plugins (Git, Docker, etc.)

iii. Configure Jenkins with required security measures.

INSTALL JENKINS ON A DEDICATED SERVER

**Update packege repository**

```
sudo apt update

```

![image](https://github.com/user-attachments/assets/0291c873-1e39-49db-bdc3-c38ebed11a59)

**Install JDK**

```
    wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
    sudo apt update
    sudo apt-get install jenkins

```
![image](https://github.com/user-attachments/assets/e04cf3c6-8fc3-4ea3-97a2-31f696282ddd)

**Add the Correct Jenkins GPG Key**

```
sudo apt install -y gnupg curl

sudo mkdir -p /usr/share/keyrings
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

```

**Install Jenkins**

```
sudo apt update

sudo apt install -y jenkins

```
**Start and Enable Jenkins Service**

```

sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins

```






