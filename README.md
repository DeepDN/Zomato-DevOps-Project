# 🚀 **DevOps Project: ZOMATO Clone App Deployment**

In this **DevOps project**, I demonstrate how to **deploy a ZOMATO Clone App** using a variety of modern DevOps tools and services.

## 🛠️ Tools & Services Used:

1. **GitHub** ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)
2. **Jenkins** ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)
3. **SonarQube** ![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat-square&logo=sonarqube&logoColor=white)
4. **Docker** ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
5. **Kubernetes** ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
6. **Prometheus** ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
7. **Grafana** ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
8. **ArgoCD** ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
9. **OWASP** ![OWASP](https://img.shields.io/badge/OWASP-000000?style=flat-square&logo=owasp&logoColor=white)
10. **Trivy** ![Trivy](https://img.shields.io/badge/Trivy-00979D?style=flat-square&logo=trivy&logoColor=white)

---

### Project Stages:

1. **Stage 1** - Deployment of App to Docker Container
2. **Stage 2** - Deployment of App to K8S Cluster with Monitoring

---

### 📂 GitHub Repo Link:  
[**ZOMATO Clone DevOps Project**](#)

### 📹 DevOps Project Video Link:  
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://youtu.be/GyoI6-I68aQ)


---

---

## Connect with me on LinkedIn:  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://in.linkedin.com/in/deepak-nemade)

---

### Feedback Request:  

After deploying the app, please share your opinion on LinkedIn along with the Project link and tag me on LinkedIn. Help the video reach wider DevOps enthusiasts.

---

## Happy learning!  
<img src="https://media.licdn.com/dms/image/v2/D4D03AQHMQDSm9Tfq2Q/profile-displayphoto-shrink_400_400/profile-displayphoto-shrink_400_400/0/1729761316154?e=2147483647&v=beta&t=abZhdf1PZikY5i4jwQoXTdSy6cmDhl_8kMtOEPvV9HM" alt="Deepak Profile Image" width="100" height="100" style="border-radius:50%;">

Deepak Nemade




# DevOps Project - Deepak: Deployment of ZOMATO Project

## Repository
[ZOMATO DevOps Project Repository](https://github.com/DeepDN/Zomato-DevOps-Project.git)

---

## Steps to Deploy

### 1. Launch an Instance
- **Configuration:** Ubuntu 24.04, t2.large, 30 GB

### 2. Connect to the Instance

### 3. Update Packages
```bash
sudo su
sudo apt update -y
```

### 4. Install AWS CLI
```bash
sudo apt install unzip -y
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### 5. Install Jenkins on Ubuntu
- Refer to [Jenkins Documentation](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu).

**Commands:**
```bash
sudo apt update -y
wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | sudo tee /etc/apt/keyrings/adoptium.asc
echo "deb [signed-by=/etc/apt/keyrings/adoptium.asc] https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list
sudo apt update -y
sudo apt install temurin-17-jdk -y
/usr/bin/java --version
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
sudo systemctl start jenkins
sudo systemctl status jenkins
```
- **Verify Jenkins Installation:** `jenkins --version`
- Open port 8080 and configure Jenkins.

### 6. Install Docker
- Refer to [Docker Documentation](https://docs.docker.com/engine/install/ubuntu/).

**Commands:**
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo usermod -aG docker ubuntu
sudo chmod 777 /var/run/docker.sock
newgrp docker
sudo systemctl status docker
```
- **Verify Docker Installation:** `docker --version`

### 7. Install Trivy
- Refer to [Trivy Documentation](https://aquasecurity.github.io/trivy/v0.55/getting-started/installation/).

**Commands:**
```bash
sudo apt-get install wget apt-transport-https gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```
- **Verify Trivy Installation:** `trivy --version`

### 8. Install Docker Scout
- Ensure DockerHub login.
- Follow the process as per video instructions.

### 9. Install SonarQube Using Docker
```bash
docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
docker ps
```
- Configure SonarQube as per video instructions.

### 10. Configure Jenkins Plugins
- Install required plugins.

### 11. SonarQube Configuration in Jenkins
- **Tools Configuration:** Follow video instructions.
- **SonarQube Token Configuration:** Create and configure credentials.

### 12. Configure DockerHub Credentials in Jenkins
- Ensure Docker images are pushed to DockerHub.

### 13. Email Notifications in Jenkins
- Configure email notifications for build updates.

### 14. System Configuration in Jenkins
- Follow video instructions.

### 15. Create a Webhook in SonarQube
- Follow video instructions.

### 16. Create a Pipeline Job in Jenkins
- Update the pipeline script for:
  - DockerHub username in stages: 'Tag and Push to DockerHub', 'DockerScoutImage', 'Deploy to Container'.
  - Email ID in the post action stage.

**Pipeline Script:**
```groovy
pipeline {
    agent any
    tools {
        jdk 'jdk17'
        nodejs 'node23'
    }
    environment {
        SCANNER_HOME=tool 'sonar-scanner'
    }
    stages {
        stage("Clean Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Git Checkout") {
            steps {
                git 'https://github.com/KastroVKiran/Zomato-Project-Kastro.git'
            }
        }
        stage("Sonarqube Analysis") {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=zomato \
                    -Dsonar.projectKey=zomato '''
                }
            }
        }
        stage("Code Quality Gate") {
            steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsId: 'Sonar-token' 
                }
            }
        }
        stage("Install NPM Dependencies") {
            steps {
                sh "npm install"
            }
        }
        stage("OWASP FS SCAN") {
            steps {
                dependencyCheck additionalArguments: '--scan ./ --disableYarnAudit --disableNodeAudit -n', odcInstallation: 'DP-Check'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage("Trivy File Scan") {
            steps {
                sh "trivy fs . > trivy.txt"
            }
        }
        stage("Build Docker Image") {
            steps {
                sh "docker build -t zomato ."
            }
        }
        stage("Tag & Push to DockerHub") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                        sh "docker tag zomato kastrov/zomato:latest "
                        sh "docker push kastrov/zomato:latest "
                    }
                }
            }
        }
        stage("Docker Scout Image") {
            steps {
                script{
                   withDockerRegistry(credentialsId: 'docker', toolName: 'docker'){
                       sh 'docker-scout quickview kastrov/zomato:latest'
                       sh 'docker-scout cves kastrov/zomato:latest'
                       sh 'docker-scout recommendations kastrov/zomato:latest'
                   }
                }
            }
        }
        stage("Deploy to Container") {
            steps {
                sh 'docker run -d --name zomato -p 3000:3000 kastrov/zomato:latest'
            }
        }
    }
    post {
        always {
            emailext attachLog: true,
                subject: "'${currentBuild.result}'",
                body: """
                <html>
                <body>
                    <div style="background-color: #FFA07A; padding: 10px; margin-bottom: 10px;">
                        <p style="color: white; font-weight: bold;">Project: ${env.JOB_NAME}</p>
                    </div>
                    <div style="background-color: #90EE90; padding: 10px; margin-bottom: 10px;">
                        <p style="color: white; font-weight: bold;">Build Number: ${env.BUILD_NUMBER}</p>
                    </div>
                    <div style="background-color: #87CEEB; padding: 10px; margin-bottom: 10px;">
                        <p style="color: white; font-weight: bold;">URL: ${env.BUILD_URL}</p>
                    </div>
                </body>
                </html>
                """,
                to: 'kastrokiran@gmail.com',
                mimeType: 'text/html',
                attachmentsPattern: 'trivy.txt'
        }
    }
}
```
- Adjust the OWASP FS SCAN stage if needed for 'UNSTABLE BUILD.'

### 17. Set Up Monitoring VMs
- Create VMs as per requirements.

