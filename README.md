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
- ﻿﻿Access the web application on your web browser.
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

**Dockerfile creation**

- Install the plugins Docker and docker pipeline

- create the dockerfile in the repository folder in github

```

# Use the official NGINX image as the base image
FROM nginx:latest

# Set the working directory in the container
WORKDIR /usr/share/nginx/html/

# Copy all files and directories from the local repository to the working directory
COPY . .

# Expose port 80 to allow external access
EXPOSE 80

```

- Grant the jenkins user permission:
  The Docker daemon requires root or docker group privileges to interact with it. You need to add the Jenkins user to the docker group

```
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

```


**Building Pipeline Script**


Below is our pipeline script:



```


pipeline {
    agent any

    environment {
        APP_NAME = "e-commerce"
        DOCKER_HUB_USER = "otigerald"
        DOCKER_IMAGE = "${DOCKER_HUB_USER}/${APP_NAME}:${env.BUILD_NUMBER}"
        APP_PORT = "8081"
    }

    triggers {
        // Trigger the pipeline on a GitHub push event
        githubPush()
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/goti13/MarketPeak_Ecommerce.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image..."
                    sh "docker build -t ${DOCKER_IMAGE} ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Stopping and removing any existing container..."
                    sh "docker stop ${APP_NAME} || true && docker rm ${APP_NAME} || true"
                    echo "Running new container..."
                    sh "docker run -d --name ${APP_NAME} -p ${APP_PORT}:80 ${DOCKER_IMAGE}"
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    echo "Logging into Docker Hub..."
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_HUB_USERNAME', passwordVariable: 'DOCKER_HUB_PASSWORD')]) {
                        sh "echo ${DOCKER_HUB_PASSWORD} | docker login -u ${DOCKER_HUB_USERNAME} --password-stdin"
                    }
                    echo "Pushing Docker image to Docker Hub..."
                    sh "docker push ${DOCKER_IMAGE}"
                }
            }
        }
    }

    post {
        success {
            echo "Docker image built and pushed successfully. Access the web application at http://<server-ip>:${APP_PORT}"
        }
        failure {
            echo "Pipeline failed. Check the logs for more details."
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
agent any → Specifies that the pipeline can run on any available agent (Jenkins worker node).

- Environment Variables
  Defines environment variables used throughout the pipeline:

```
environment {
    APP_NAME = "e-commerce"
    DOCKER_HUB_USER = "otigerald"
    DOCKER_IMAGE = "${DOCKER_HUB_USER}/${APP_NAME}:${env.BUILD_NUMBER}"
    APP_PORT = "8081"
}

```

APP_NAME: Name of the application (used for naming the Docker container and image).
DOCKER_HUB_USER: Your Docker Hub username.
DOCKER_IMAGE: The Docker image name and tag, formatted as <DOCKER_HUB_USER>/<APP_NAME>:<BUILD_NUMBER>.
APP_PORT: The port on which the application will run (mapped to port 80 in the container).


- Triggers

```

triggers {
    // Trigger the pipeline on a GitHub push event
    githubPush()
}

```

Automatically triggers the pipeline when a push event occurs on the GitHub repository.


- Stages


```

stage('Clone Repository') {
    steps {
        git branch: 'main', url: 'https://github.com/goti13/MarketPeak_Ecommerce.git'
    }
}

```
Clones the GitHub repository (MarketPeak_Ecommerce) from the main branch.

- Build Docker Image

```
stage('Build Docker Image') {
    steps {
        script {
            echo "Building Docker image..."
            sh "docker build -t ${DOCKER_IMAGE} ."
        }
    }
}

```

Builds a Docker image using the Dockerfile in the repository.  <br>
Tags the image with the name and version specified in DOCKER_IMAGE.

- Run Docker Container

```
stage('Run Docker Container') {
    steps {
        script {
            echo "Stopping and removing any existing container..."
            sh "docker stop ${APP_NAME} || true && docker rm ${APP_NAME} || true"
            echo "Running new container..."
            sh "docker run -d --name ${APP_NAME} -p ${APP_PORT}:80 ${DOCKER_IMAGE}"
        }
    }
}

```

Stops and removes any existing container with the same name (APP_NAME).  <br> 
Runs a new Docker container using the built image:  <br> 
-d: Runs the container in detached mode (in the background).  <br>
--name ${APP_NAME}: Names the container.  <br>
-p ${APP_PORT}:80: Maps port 8081 on the host to port 80 in the container.


- Push to Docker Hub

```
stage('Push to Docker Hub') {
    steps {
        script {
            echo "Logging into Docker Hub..."
            withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_HUB_USERNAME', passwordVariable: 'DOCKER_HUB_PASSWORD')]) {
                sh "echo ${DOCKER_HUB_PASSWORD} | docker login -u ${DOCKER_HUB_USERNAME} --password-stdin"
            }
            echo "Pushing Docker image to Docker Hub..."
            sh "docker push ${DOCKER_IMAGE}"
        }
    }
}

```

Logs into Docker Hub using credentials stored in Jenkins (docker-hub-credentials).  <br>
Pushes the Docker image to Docker Hub.


- Post Actions

Success

```

post {
    success {
        echo "Docker image built and pushed successfully. Access the web application at http://<server-ip>:${APP_PORT}"
    }
}

```
Prints a success message with the URL to access the application.

Failure

```

failure {
    echo "Pipeline failed. Check the logs for more details."
}

```

Prints a failure message if the pipeline fails.

**How the Pipeline Works**

1. Trigger:
   
 - The pipeline is triggered by a push to the main branch of the GitHub repository.
   
2. Clone Repository:
   
 - The repository is cloned to the Jenkins workspace.
   
3. Build Docker Image:
   
 - A Docker image is built using the Dockerfile in the repository.
   
4. Run Docker Container:
   
 - Any existing container with the same name is stopped and removed.
   
 - A new container is started using the built image.
   
5. Push to Docker Hub:
   
 - The Docker image is pushed to Docker Hub for later use or deployment.
      
6. Post Actions:
   
 - If the pipeline succeeds, a success message is printed.
   
 - If the pipeline fails, a failure message is printed.


**Key Points**

- Environment Variables:
  DOCKER_IMAGE dynamically includes the build number, ensuring unique tags for each build.
  APP_PORT allows you to map the container port to a specific host port.

- Docker Commands:
  docker build: Builds the image.
  docker run: Runs the container.
  docker push: Pushes the image to Docker Hub.

- Error Handling:
  The || true in docker stop and docker rm ensures that the pipeline continues even if no container exists to stop or remove.

- Credentials:
  Docker Hub credentials are securely managed using Jenkins credentials.

  
**Save the pipepline script**


From the dashboard menu on the left side, click on new item


<img width="1439" alt="image" src="https://github.com/user-attachments/assets/cbc2e63e-8eb2-4674-803b-6935c477250b" />


Create a pipeline job and name it "CapstonePipelineJob"


<img width="1184" alt="image" src="https://github.com/user-attachments/assets/a4524f46-b5b9-4c9e-aa4e-1541ae54fa8d" />


**Configure Build Trigger**

Click "Configure" your job and add this configurations

Click on build trigger to configure triggering the job from GitHub webhook

<img width="1228" alt="image" src="https://github.com/user-attachments/assets/efac06ce-eb67-4171-a543-ba9790813065" />


Create a github webhook using jenkins ip address and port


<img width="1173" alt="image" src="https://github.com/user-attachments/assets/e1a0f685-4567-406a-9af3-af0939e416c0" />


Paste the pipeline script above into the pipeline section and save.


<img width="1409" alt="image" src="https://github.com/user-attachments/assets/f21d3985-d289-45ea-a2e0-9e0b13c0c41b" />


Login to your docker registry (https://hub.docker.com/repositories/) and create a new repository 


<img width="1434" alt="image" src="https://github.com/user-attachments/assets/1856dc96-2aa1-428d-81a4-54d783c86788" />


The name of the repository must same with value= "e-commerce" from our pipeline script


<img width="1430" alt="image" src="https://github.com/user-attachments/assets/d8335c78-6497-4ab9-a196-3fdf74e551b2" />



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


**Accessing our Application on web browser**


To access the index.html of our application file on our web browser, we need to first edit the inbound rules and open the port we mapped our container to (8081)


<img width="1434" alt="image" src="https://github.com/user-attachments/assets/eb8dd13a-963a-4970-b332-d21ccce93ad8" />




