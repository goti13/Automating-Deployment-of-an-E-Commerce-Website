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


On our Jenkins instance, create new inbound rules for port 8080 in security group
By default, jenkins listens on port 8080, we need create an inbound rule for this in the security group of our jenkins instance

<img width="1438" alt="image" src="https://github.com/user-attachments/assets/0a906882-3738-41cf-bd50-7360821012e4" />


Open Jenkins in your browser:

```

http://<your-server-ip>:8080

```

You can retrieve the server ip address with the command:

```

curl ifconfig.me

```

![image](https://github.com/user-attachments/assets/c6e944b6-84b3-41ff-9e64-1675116937b9)


**Unlock Jenkins**

To get the admin password, run:

```

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

```

![image](https://github.com/user-attachments/assets/95198e5b-7a74-42fb-837f-8fb241aec8db)



Install Suggested plugins

![image](https://github.com/user-attachments/assets/5f84fd80-c278-4a70-be7d-4fcb8215787e)

Create Admin User

![image](https://github.com/user-attachments/assets/40fa0de9-1a93-4f84-ab99-dc60f558b87a)

Login to Jenkins Console

![image](https://github.com/user-attachments/assets/90412701-8154-42e2-a82d-ad39d56e322e)


2. Source Code Management Repository Integration

**Objective: Connect Jenkins to the version control system for source code management.**


Steps:

i. Integrate Jenkins with the source code management repository (GitHub)

ii. Configure webhooks for automatic triggering of Jenkins builds.

Creating a Freestyle Project

From the dashboard menu on the left side, click on new item

<img width="1425" alt="image" src="https://github.com/user-attachments/assets/83c49d60-6be1-40d6-9e9e-4c868e611352" />

 
 Create a freestyle project and name it "Capstone Job"

<img width="1418" alt="image" src="https://github.com/user-attachments/assets/15fb195b-a88b-4694-96a6-8f999b986dc8" />

**Connecting Jenkins To Our Source Code Management**

For this project we will be using an exiting [repository](https://github.com/goti13/MarketPeak_Ecommerce)  MarketPeak_Ecommerce                

Connect "jenkins' to 'MarketPeak_Ecommerce' repository by pasting the repository url in the area selected below. Make sure your current branch is 'main'

<img width="1432" alt="image" src="https://github.com/user-attachments/assets/0508a8f4-d9c8-4153-9051-9049b48b24ec" />

Select "Git" as the Source code management, paste the repository url in its field and use "*/main" as the Branch specifier 

<img width="1344" alt="image" src="https://github.com/user-attachments/assets/aab23453-3c96-4c34-8104-d6926fff2e06" />

Save configuration and run "build now" to connect jenkins to our repository

<img width="1431" alt="image" src="https://github.com/user-attachments/assets/e0e0c418-2f68-47f8-b3e1-78433b1cea6a" />

We have successfully connected jenkins with our github repository (MarketPeak_Ecommerce)

**Configuring Build Trigger**

Click "Configure" your job and add this configurations

<img width="1428" alt="image" src="https://github.com/user-attachments/assets/84a07cea-9c69-4ec3-ab71-a380945ce855" />

Click on build trigger to configure triggering the job from GitHub webhook

<img width="1222" alt="image" src="https://github.com/user-attachments/assets/a615aeef-2598-4365-8275-a6307cfa47c6" />

Create a github webhook using jenkins ip address and port

<img width="1163" alt="image" src="https://github.com/user-attachments/assets/87722466-f5e9-4891-95c0-fb4310f2223c" />


<img width="1188" alt="image" src="https://github.com/user-attachments/assets/ace66165-8ee5-4af0-925c-54f1e6f2457e" />


3. Jenkins Freestyle Jobs for Build and Unit Tests




4. Jenkins Pipeline for Web Application
   
Objective: Develop a Jenkins Pipeline for running a web application.

Steps:

Create a Jenkins Pipeline script to run a web application.


Below is a Jekins pipeline script to run a web application:

```

pipeline {
    agent any

    stages {
        stage('Connect To Github') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/goti13/jenkins-scm.git']])
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t myapp .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -itd -p 8081:80 myapp'
                }
            }
        }
    }
}


```

5. Docker Image Creation and Registry Push

Objective: To Automate the creation of Docker images for the web application and push them to a container registry docker hub.

Steps:

- Configure Jenkins to build Docker images.
- ﻿﻿Run a container using the built docker image
- ﻿﻿Access the web application on your we browser.
- ﻿﻿Push Docker images to a container registry.


**Installing Docker**

Before jenkins can run docker commands, we need to install docker on the same instance jenkins was installed. From our shell scripting knowledge, let's install docker with shell script

Create a file named docker.sh

Open the file and paste the script below

```

#!/bin/bash

# Exit on any error
set -e

echo "Updating system packages..."
sudo apt update -y
sudo apt upgrade -y

echo "Installing required dependencies..."
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common gnupg

echo "Adding Docker’s official GPG key..."
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "Adding Docker repository..."
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

echo "Updating package index..."
sudo apt update -y

echo "Installing Docker..."
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin

echo "Starting and enabling Docker service..."
sudo systemctl start docker
sudo systemctl enable docker

echo "Adding current user to Docker group..."
sudo usermod -aG docker $USER

echo "Docker installation completed successfully!"
echo "Log out and log back in to apply group changes."
docker --version


```

Save and close the file

Make the file executable


```
chmod u+x docker.sh

```

Execute the script

```
./docker.sh

```

**Building Pipeline Script**


Below is our pipeline script:



```


pipeline {
    agent any

    environment {
        APP_NAME = "marketpeak_ecommerce"
        COMMIT_HASH = sh(script: 'git rev-parse --short HEAD', returnStdout: true).trim()
        BUILD_ID = env.BUILD_NUMBER
        DOCKER_IMAGE = "your-dockerhub-username/marketpeak:$BUILD_ID-$COMMIT_HASH"
        APP_PORT = "8081"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/goti13/MarketPeak_Ecommerce.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Run Application') {
            steps {
                sh 'docker stop $APP_NAME || true && docker rm $APP_NAME || true'
                sh 'docker run -d --name $APP_NAME -p $APP_PORT:80 $DOCKER_IMAGE'
            }
        }

        stage('Push to DockerHub') {
            when {
                branch 'main'
            }
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://hub.docker.com/repository/docker/otigerald/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }

    post {
        success {
            echo "Application is running at http://<server-ip>:8081"
        }
        failure {
            echo "Build failed. Check logs!"
        }
    }
}


```



**Explaining the script**

- Pipeline Structure

```
pipeline {
    agent any

```

pipeline {} → Defines a Jenkins declarative pipeline.   <br> 
agent any → The pipeline can run on any available agent.

- Environment Variables

```
environment {
    APP_NAME = "marketpeak_ecommerce"
    COMMIT_HASH = sh(script: 'git rev-parse --short HEAD', returnStdout: true).trim()
    BUILD_ID = env.BUILD_NUMBER
    DOCKER_IMAGE = "your-dockerhub-username/marketpeak:$BUILD_ID-$COMMIT_HASH"
    APP_PORT = "8081"
}

```

APP_NAME → The name of the running container.
COMMIT_HASH → Gets the short commit hash of the latest commit.
BUILD_ID → Jenkins build number (unique per build).
DOCKER_IMAGE → Defines the Docker image name and tags it uniquely using BUILD_ID and COMMIT_HASH.
(Example: your-dockerhub-username/marketpeak:15-a1b2c3d where 15 is the build number, and a1b2c3d is the commit hash.)
APP_PORT → Exposes the application on port 8081.


- Pipeline Stages

```
stage('Clone Repository') {
    steps {
        git 'https://github.com/goti13/MarketPeak_Ecommerce.git'
    }
}


```

Pulls the source code from GitHub.


- Build Docker Image


```

stage('Build Docker Image') {
    steps {
        sh 'docker build -t $DOCKER_IMAGE .'
    }
}

```

- Run Application

```
stage('Run Application') {
    steps {
        sh 'docker stop $APP_NAME || true && docker rm $APP_NAME || true'
        sh 'docker run -d --name $APP_NAME -p $APP_PORT:80 $DOCKER_IMAGE'
    }
}

```

Stops & removes any running container with the same name (APP_NAME).    <br> 
Runs the application inside a Docker container.    <br> 
Maps port 8081 (APP_PORT) on the server to port 80 inside the container.   

- Push to DockerHub (Only for main Branch)

```
stage('Push to DockerHub') {
    when {
        branch 'main'
    }
    steps {
        withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://hub.docker.com/repository/docker/otigerald/']) {
            sh 'docker push $DOCKER_IMAGE'
        }
    }
}

```

Runs only if the branch is main (when { branch 'main' }).    <br> 
Authenticates with DockerHub using credentials stored in Jenkins (docker-hub-credentials).    <br> 
Pushes the built image to the DockerHub repository.   

- Post-Build Actions

```

post {
    success {
        echo "Application is running at http://<server-ip>:8081"
    }
    failure {
        echo "Build failed. Check logs!"
    }
}

```

If the pipeline succeeds, it prints "Application is running at http://<server-ip>:8081".    <br> 
If the pipeline fails, it prints "Build failed. Check logs!".

- Key Takeaways

Every build creates a uniquely tagged Docker image using $BUILD_ID and $COMMIT_HASH.    <br> 
Runs the application in a Docker container and exposes it on port 8081.    <br> 
Only pushes to DockerHub when running on the main branch.    <br> 
Uses stored credentials (docker-hub-credentials) to authenticate with DockerHub.   

- What Happens When You Push a Change?

Webhook triggers Jenkins.    <br> 
Jenkins pulls the latest code.    <br> 
Jenkins builds a new Docker image.    <br> 
Jenkins runs the container.    <br> 
If the branch is main, Jenkins pushes the image to DockerHub.    <br> 
Jenkins prints the application URL if successful.   

**Save the pipepline script**


<img width="1435" alt="image" src="https://github.com/user-attachments/assets/bb306fca-a4ff-4438-b4bf-cb1ed2c514b4" />


<img width="1340" alt="image" src="https://github.com/user-attachments/assets/4cc0d95a-11f1-46b7-b9dd-d663b3dd7498" />




<img width="1320" alt="image" src="https://github.com/user-attachments/assets/6b73ee6c-6702-44c8-ab13-8cd21aef491a" />




**Store DockerHub Credentials in Jenkins**

Go to Manage Jenkins → Manage Credentials. → Click (global) under "Stores scoped to Jenkins". → Click Add Credentials (on the left). 


<img width="1420" alt="image" src="https://github.com/user-attachments/assets/1af76995-9430-4c25-badf-05bd22671d8c" />


<img width="1425" alt="image" src="https://github.com/user-attachments/assets/9e73cfee-46de-4be1-91ae-0b7903961eb1" />


<img width="1429" alt="image" src="https://github.com/user-attachments/assets/4c7846c1-bd96-4429-af28-615b2dad5744" />



Select:

Kind: Username with password  <br>
Scope: Global
Username: (Your DockerHub username)  <br>
Password: (Your DockerHub password or access token)  <br>
ID: docker-hub-credentials (This is the ID used in the pipeline)  <br>
Description: "DockerHub Credentials"


<img width="1148" alt="image" src="https://github.com/user-attachments/assets/aca90be5-55c8-4f27-86a9-a1d7bf8eb165" />




