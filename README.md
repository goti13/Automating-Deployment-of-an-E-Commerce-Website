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
sudo apt update && sudo apt upgrade -y

```

![image](https://github.com/user-attachments/assets/bcf64edf-2e04-419c-849d-65af2ebdcda8)


**Install Java**

```
sudo apt install -y openjdk-17-jdk

```

![image](https://github.com/user-attachments/assets/3eaf0b47-267f-415b-80e1-bc1e8708620b)


**Verify Java installation**

```

java -version

```

You should have an output similar to:


![image](https://github.com/user-attachments/assets/411e1674-98d0-4cd2-bb18-f5a1255b622b)


**Add Jenkins Repository Key**

```
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

```

![image](https://github.com/user-attachments/assets/b5399c02-f52f-416e-8a46-49590be492f7)

**Add Jenkins Key**

```

echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

```

![image](https://github.com/user-attachments/assets/e5ffa758-b6d1-4f4a-bec5-32ed7e580158)


**Install Jenkins**

```
sudo apt update
sudo apt install -y jenkins

```

![image](https://github.com/user-attachments/assets/986c5636-3ea7-437b-9316-0bd5eaddd3fe)


**Start and Enable Jenkins Service**

```
sudo systemctl start jenkins

```

Enable Jenkins

```
sudo systemctl enable jenkins

```

![image](https://github.com/user-attachments/assets/d121f3fd-b6ce-4a03-88fd-16be7a164d2b)


Check the status of Jenkins

```

sudo systemctl status jenkins

```


If it's working, you should see:

![image](https://github.com/user-attachments/assets/30b373ca-cb7a-4c8b-9b99-bb12c4b0b4b9)







