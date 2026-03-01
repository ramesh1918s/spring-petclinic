                                    Petclinic Project 😊


Project Workflow

<<<<<<< HEAD
=======
See the presentation here:  
[Spring Petclinic Sample Application (legacy slides)](https://speakerdeck.com/michaelisvy/spring-petclinic-sample-application?slide=20)

> **Note:** These slides refer to a legacy, pre–Spring Boot version of Petclinic and may not reflect the current Spring Boot–based implementation.  
> For up-to-date information, please refer to this repository and its documentation.

>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5


<<<<<<< HEAD
=======
Spring Petclinic is a [Spring Boot](https://spring.io/guides/gs/spring-boot) application built using [Maven](https://spring.io/guides/gs/maven/) or [Gradle](https://spring.io/guides/gs/gradle/).
Java 17 or later is required for the build, and the application can run with Java 17 or newer.

You first need to clone the project locally:
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5

Step 1: Create EC2 Instance type is t2-Large Install  All Dependencies

EC2 install create connect putty to install 

To Install jenkins used this commands

sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins


sudo systemctl enable jenkins
sudo systemctl start jenkins

sudo systemctl status jenkins

http://public-ip:8080/

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Past the Password
Add username and password 
Jenkins Page open ok its 

To install AWS-cli

sudo snap install aws-cli --classic
aws configure

Access_key :xxxxxxxxxxxxxxx
Security_key:xxxxxxxxxxxxxxxxx

Maven Install 

sudo apt install maven -y
 mvn  -version


Kubectl install

curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl && sudo mv kubectl /usr/local/bin/

kubectl version --client


 Eksctl Install

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz
sudo mv eksctl /usr/local/bin

eksctl version


Install Docker 

sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
newgrp docker

sudo usermod -aG docker jenkins


Git Clone My github repo for petclinic project

git clone https://github.com/ramesh1918s/spring-petclinic.git
cd spring-petclinic
<<<<<<< HEAD
ls

ubuntu@ip-191-43-1-66:~/spring-petclinic$ ls
Dockerfile  LICENSE.txt  README.md  build.gradle  docker-compose.yml  gradle  gradlew  gradlew.bat  k8s  mvnw  mvnw.cmd  pom.xml  settings.gradle  src
=======
```
If you are using Maven, you can start the application on the command-line as follows:

```bash
./mvnw spring-boot:run
```
With Gradle, the command is as follows:

```bash
./gradlew bootRun
```
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5

GitHub Login

git config --global user.name "ramesh1918s"
git config --global user.email "shivaram915454@gmail.com"

<<<<<<< HEAD

To Install SonarQube through docker image 

docker run -d \
  --name sonar \
  -p 9000:9000 \
  sonarqube:lts-community
=======
You can, of course, run Petclinic in your favorite IDE.
See below for more details.
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5




ubuntu@ip-191-43-1-66:~$ docker ps
a824eec03581   sonarqube:lts-community   "/opt/sonarqube/dock…"   About an hour ago   Up About an hour   0.0.0.0:9000->9000/tcp, :::9000->9000/tcp   sonar

Step 2: Setup All Dependencies

Step for SonarQube 

http://<EC2_PUBLIC_IP>:9000

Default Login user_name: admin
Default Password: admin
Login SonarQube page 

To generate one token 
Go to Administration below security below user administration /token/name of token to generate token 
Ex: squ_55d9552d37fe31c6fa19510836910a4104be0373
Ok its 
squ_f861be9d999b9049f7d5d048154fb8d48062ee6b
Jenkins Setup for Sonarqube install  SonarQube Scanner for Jenkins plugin

<<<<<<< HEAD
Go to Jenkins → Manage Jenkins  Plugins - Available plugins Search (Sonarqube) 
→ Configure System
Add your SonarQube instance under SonarQube servers
=======
```bash
docker run -e MYSQL_USER=petclinic -e MYSQL_PASSWORD=petclinic -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:9.5
```
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5


<<<<<<< HEAD
Name: SonarQube
=======
```bash
docker run -e POSTGRES_USER=petclinic -e POSTGRES_PASSWORD=petclinic -e POSTGRES_DB=petclinic -p 5432:5432 postgres:18.1
```
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5


Server URL: http://54.167.235.121:9000


Token: use sqp_... from above
Jenkins - credentials  global add security text 
add password (sqp_d3a1452243e70e8814ae03cfe4fbe01ac7940e42) add name-id sonar-token ,  sonar-token 
save ok 
Jenkins  Maven setup→ Global Tool Configuration:

Maven installation named Maven3
( Ensure this is configured in Jenkins → Global Tool Configuration)
Ok save 

Webhooks → Add webhook

Payload URL:
http://<your-public-ip>:8080/github-webhook/
Content type:
application/json
Secret: (optional, for added security)
Events to trigger:

Step 3:Jenkins CI Pipeline 

Git checkout
Sonarqube code quality 
Maven Build Package

Project name: Petclinic
Add pipeline Script 
GitHub hook trigger for GITScm polling
Given Below My pipeline script 

pipeline {
    agent any

    tools {
        maven 'Maven3'  
    }

<<<<<<< HEAD
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ramesh1918s/spring-petclinic.git'
            }
        }
=======
- Java 17 or newer (full JDK, not a JRE)
- [Git command line tool](https://help.github.com/articles/set-up-git)
- Your preferred IDE
  - Eclipse with the m2e plugin. Note: when m2e is available, there is a m2 icon in `Help -> About` dialog. If m2e is
  not there, follow the installation process [here](https://www.eclipse.org/m2e/)
  - [Spring Tools Suite](https://spring.io/tools) (STS)
  - [IntelliJ IDEA](https://www.jetbrains.com/idea/)
  - [VS Code](https://code.visualstudio.com)
>>>>>>> e316074300de4761f7b100a21423525e8b8ecdc5

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {  // This name must match Jenkins SonarQube config
                    sh '''
                        mvn clean verify sonar:sonar \
                          -Dsonar.projectKey=petclinic
                    '''
                }
            }
        }

        stage('Build Package') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
    }
}



Build Success



petclinic
Add description
SonarQube Quality Gate
petclinicPassed
server-side processing:success
Git Checkout
Maven Build
SonarQube Code Analysis
 
To SonarQube Page

http://54.167.235.121:9000/ 




Step 4:Jenkins CD Part Docker Image Build & Push

To Install trivy 
This trivy tool to scan the docker images 

sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy       
 
trivy --version

Scan the image  Ex: trivy image <iimagename:tagename>
trivy image shivaram1918/spring-petclinic-1:latest


CD_Process In Jenkins


Jenkins → Add Credentials for Docker Hub

Go to: Jenkins Dashboard → Manage Jenkins → Manage Credentials → (global)

Then: Add Credentials → Username & Password
Username: shivaram1918
Password: your Docker Hub password

ID: docker hub-creds

 Add jenkins to docker group (terminal)

sudo usermod -aG docker jenkins

Restart Jenkins

sudo systemctl restart jenkins

(Optional) Restart Docker too

sudo systemctl restart docker

Jenkins CD  Pipeline  


pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
        DOCKER_IMAGE = "shivaram1918/spring-petclinic-8"
        IMAGE_TAG = "v3"
    }

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'ramesh1918s-patch-1', url: 'https://github.com/ramesh1918s/spring-petclinic.git'
            }
        }

        stage('Debug Java') {
            steps {
                sh '''
                    echo "JAVA_HOME=$JAVA_HOME"
                    java -version
                    mvn -version
                '''
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn clean verify -DskipTests sonar:sonar -Dsonar.projectKey=petclinic'
                }
            }
        }

        stage('Build Package') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:$IMAGE_TAG .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Dockerkey', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                        docker push $DOCKER_IMAGE:$IMAGE_TAG
                    '''
                }
            }
        }

        stage("TRIVY") {
            steps {
                sh "trivy image $DOCKER_IMAGE:$IMAGE_TAG > trivyimage.txt"
            }
        }

        stage('Deploy to container') {
            steps {
                sh '''
                    docker rm -f petclinic4 || true
                    docker run -d --name petclinic4 -p 8083:8080 $DOCKER_IMAGE:$IMAGE_TAG
                '''
            }
        }
    }
}



sudo usermod -aG docker jenkins

sudo systemctl restart jenkins

sudo systemctl status docker

docker logs 66a80771c6da

To Pull image Docker Hub 

shivaram1918/spring-petclinic




EKS Cluster Creating

eksctl create cluster \
--name ram-eks \
--region eu-north-1 \
--nodegroup-name ram-nodes \
--node-type t3.medium \
--nodes 2 \
--nodes-min 1 \
--nodes-max 3 \
--managed

Cluster not created by using terraform main.tf files before that we need to install terraform first your ec2 instance




git clone https://github.com/hashicorp-education/learn-terraform-provision-eks-cluster

Check the region and changes the region also default region is us-east-2 and changes  as per your region


Terraform init
Terraform plan
Terraform apply

aws eks update-kubeconfig \
  --region us-east-2 \
  --name ram-eks # update your cluster name




 aws eks --region eu-north-1 update-kubeconfig --name ram-eks

 kubectl get nodes


Step 5: Monitoring

Install Prometheus and Grafana:

Set up Prometheus and Grafana to monitor your application.

Installing Prometheus:

First, create a dedicated Linux user for Prometheus and download Prometheus:

sudo useradd --system --no-create-home --shell /bin/false prometheus
wget https://github.com/prometheus/prometheus/releases/download/v2.47.1/prometheus-2.47.1.linux-amd64.tar.gz


Extract Prometheus files, move them, and create directories:

tar -xvf prometheus-2.47.1.linux-amd64.tar.gz
cd prometheus-2.47.1.linux-amd64/
sudo mkdir -p /data /etc/prometheus
sudo mv prometheus promtool /usr/local/bin/
sudo mv consoles/ console_libraries/ /etc/prometheus/
sudo mv prometheus.yml /etc/prometheus/prometheus.yml

Set ownership for directories:

sudo chown -R prometheus:prometheus /etc/prometheus/ /data/

Create a systemd unit configuration file for Prometheus:

sudo nano /etc/systemd/system/prometheus.service

Add the following content to the prometheus.service file:

[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=prometheus
Group=prometheus
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/data \
  --web.console.templates=/etc/prometheus/consoles \
  --web.console.libraries=/etc/prometheus/console_libraries \
  --web.listen-address=0.0.0.0:9090 \
  --web.enable-lifecycle

[Install]
WantedBy=multi-user.target


Save and Exit

Here's a brief explanation of the key parts in this prometheus.service file:

User and Group specify the Linux user and group under which Prometheus will run.

ExecStart is where you specify the Prometheus binary path, the location of the configuration file (prometheus.yml), the storage directory, and other settings.

web.listen-address configures Prometheus to listen on all network interfaces on port 9090.

web.enable-lifecycle allows for management of Prometheus through API calls.

Enable and start Prometheus:

sudo systemctl enable prometheus
sudo systemctl start prometheus


Verify Prometheus's status:

sudo systemctl status prometheus

You can access Prometheus in a web browser using your server's IP and port 9090:

http://<your-server-ip>:9090




Installing Node Exporter:

Create a system user for Node Exporter and download Node Exporter:

sudo useradd --system --no-create-home --shell /bin/false node_exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.6.1/node_exporter-1.6.1.linux-amd64.tar.gz

Extract Node Exporter files, move the binary, and clean up:

tar -xvf node_exporter-1.6.1.linux-amd64.tar.gz
sudo mv node_exporter-1.6.1.linux-amd64/node_exporter /usr/local/bin/
rm -rf node_exporter*

Create a systemd unit configuration file for Node Exporter:

sudo nano /etc/systemd/system/node_exporter.service

Add the following content to the node_exporter.service file:

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

StartLimitIntervalSec=500
StartLimitBurst=5

[Service]
User=node_exporter
Group=node_exporter
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/node_exporter --collector.logind

[Install]
WantedBy=multi-user.target
Replace --collector.logind with any additional flags as needed.

Enable and start Node Exporter:

sudo systemctl enable node_exporter
sudo systemctl start node_exporter

Verify the Node Exporter's status:

sudo systemctl status node_exporter

You can access Node Exporter metrics in Prometheus.

You can access Node Exporter metrics in Prometheus.

Configure Prometheus Plugin Integration:


Integrate Jenkins with Prometheus to monitor the CI/CD pipeline.

Prometheus Configuration:

To configure Prometheus to scrape metrics from Node Exporter and Jenkins, you need to modify the prometheus.yml file. Here is an example prometheus.yml configuration for your setup:

global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'jenkins'
    metrics_path: '/prometheus'
    static_configs:
      - targets: ['<your-jenkins-ip>:<your-jenkins-port>']



Make sure to replace <your-jenkins-ip> and <your-jenkins-port> with the appropriate values for your Jenkins setup.

Check the validity of the configuration file:

promtool check config /etc/prometheus/prometheus.yml

Reload the Prometheus configuration without restarting:

curl -X POST http://localhost:9090/-/reload
You can access Prometheus targets at:

http://<your-prometheus-ip>:9090/targets


Install Grafana


Install Grafana on Ubuntu 22.04 and Set it up to Work with Prometheus

Step 1: Install Dependencies:

First, ensure that all necessary dependencies are installed:

sudo apt-get update
sudo apt-get install -y apt-transport-https software-properties-common

Step 2: Add the GPG Key:
Add the GPG key for Grafana:
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -


Step 3: Add Grafana Repository:

Add the repository for Grafana stable releases:

echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

Step 4: Update and Install Grafana:

Update the package list and install Grafana:

sudo apt-get update
sudo apt-get -y install grafana

Step 5: Enable and Start Grafana Service:

To automatically start Grafana after a reboot, enable the service:

sudo systemctl enable grafana-server

Then, start Grafana:

sudo systemctl start grafana-server

Step 6: Check Grafana Status:

Verify the status of the Grafana service to ensure it's running correctly:

sudo systemctl status grafana-server

Step 7: Access Grafana Web Interface:
Open a web browser and navigate to Grafana using your server's IP address. The default port for Grafana is 3000. For example:

http://<your-server-ip>:3000


You'll be prompted to log in to Grafana. The default username is "admin," and the default password is also "admin."

Step 8: Change the Default Password:

When you log in for the first time, Grafana will prompt you to change the default password for security reasons. Follow the prompts to set a new password.

Step 9: Add Prometheus Data Source:
To visualize metrics, you need to add a data source. Follow these steps:
Click on the gear icon (⚙️) in the left sidebar to open the "Configuration" menu.
Select "Data Sources."
Click on the "Add data source" button.
Choose "Prometheus" as the data source type.
In the "HTTP" section:
Set the "URL" to http://localhost:9090 (assuming Prometheus is running on the same server).
Click the "Save & Test" button to ensure the data source is working.

Step 10: Import a Dashboard:
To make it easier to view metrics, you can import a pre-configured dashboard. Follow these steps:
Click on the "+" (plus) icon in the left sidebar to open the "Create" menu.
Select "Dashboard."
Click on the "Import" dashboard option.
Enter the dashboard code you want to import (e.g., code 1860).
Click the "Load" button.
Select the data source you added (Prometheus) from the dropdown.
Click on the "Import" button.
You should now have a Grafana dashboard set up to visualize metrics from Prometheus.
Grafana is a powerful tool for creating visualizations and dashboards, and you can further customize it to suit your specific monitoring needs.
That's it! You've successfully installed and set up Grafana to work with Prometheus for monitoring and visualization.
Configure Prometheus Plugin Integration:
Integrate Jenkins with Prometheus to monitor the CI/CD pipeline.



Phase 5: Notification
Implement Notification Services:
Set up email notifications in Jenkins or other notification mechanisms.








Helm install ubuntu


curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null

sudo apt-get install apt-transport-https --yes

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list

sudo apt-get update

sudo apt-get install helm


Argocd install 

https://argo-cd.readthedocs.io/en/stable/getting_started/
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Expose the argocd

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'



Solution Options: (error vaste uninstall )
Option 1: Uninstall and Install Fresh

helm uninstall prometheus-node-exporter --namespace prometheus-node-exporter



helm install prometheus-node-exporter prometheus-community/prometheus-node-exporter --namespace prometheus-node-exporter

export ARGOCD_SERVER=$(kubectl get svc argocd-server -n argocd -o json | jq --raw-output '.status.loadBalancer.ingress[0].hostname')


a0a3e79d4a3ca447b865b968057718f1-1725549611.eu-north-1.elb.amazonaws.com



Copy AND POST IN GOOGLE

Expose the Password

export ARGOCD_PWD=$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)
echo "ArgoCD admin password: $ARGOCD_PWD"









( Optional )Just apply commands and prometheus.yml file edits add script in file
ubuntu@ip-196-32-11-181:/etc/prometheus$ sudo cat prometheus.yml
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["localhost:9090"]




  - job_name: 'node_exporter'
    static_configs:
      - targets: ['51.21.248.91:9100']

  - job_name: 'jenkins'
    metrics_path: '/prometheus'
    static_configs:
      - targets: ['51.21.248.91:8080']


  - job_name: 'k8s'
    metrics_path: '/metrics'
    static_configs:
      - targets: ['51.21.248.91:9100']


ubuntu@ip-196-32-11-181:/etc/prometheus$ sudo nano prometheus.yml
ubuntu@ip-196-32-11-181:/etc/prometheus$ sudo promtool check config /etc/prometheus/prometheus.yml
Checking /etc/prometheus/prometheus.yml
 SUCCESS: /etc/prometheus/prometheus.yml is valid prometheus config file syntax





ubuntu@ip-196-32-11-181:/etc/prometheus$ curl -X POST http://localhost:9090/-/reload
ubuntu@ip-196-32-11-181:/etc/prometheus$ sudo nano prometheus.yml
ubuntu@ip-196-32-11-181:/etc/prometheus$ sudo promtool check config /etc/prometheus/prometheus.yml
Checking /etc/prometheus/prometheus.yml
 SUCCESS: /etc/prometheus/prometheus.yml is valid prometheus config file syntax

ubuntu@ip-196-32-11-181:/etc/prometheus$ curl -X POST http://localhost:9090/-/reload
ubuntu@ip-196-32-11-181:/etc/prometheu






eksctl delete cluster --name ram-eks --region eu-north-1


               Successfully Completed😀

—---------------------completed—--------------------------------

(This is Additional work info)
Check Disk Usage
SSH lo run cheyyi:
df -h

Chudali / or /var (Jenkins usually /var/lib/jenkins) usage ekkuva unda?

2. Check Jenkins Workspace Size

sudo du -sh /var/lib/jenkins/*

Large folders:
/var/lib/jenkins/workspace


/var/lib/jenkins/jobs


/var/lib/jenkins/.m2


/var/lib/jenkins/.docker



3. Clean Old Jenkins Builds
Jenkins UI lo:
Go to each job → Configure


Set Discard Old Builds (e.g., keep only last 5 builds)


OR terminal lo:
bash
CopyEdit
sudo rm -rf /var/lib/jenkins/workspace/*    # Cleanup old workspaces


4. Clean Docker
Docker images & containers disk ni chala occupy chestayi:
# Remove stopped containers
docker container prune -f

# Remove unused images
docker image prune -a -f

# Remove unused volumes
docker volume prune -f


 5. Mount Additional Volume (If needed)
If you’re on EC2 with low disk (like 8GB), upgrade cheyyali:
Stop EC2 instance


Increase EBS volume size (e.g., from 8GB → 30GB)


Start again




sudo growpart /dev/xvda 1
sudo resize2fs /dev/xvda1



 6. Move Jenkins Home (Optional)
If root partition full aipotundi:

sudo mv /var/lib/jenkins /mnt/jenkins
sudo ln -s /mnt/jenkins /var/lib/jenkins


Deploy Application EKS 

Install eksctl (if not done)
curl --silent --location "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin
eksctl version


eksctl create cluster \
--name ram-eks \
--region us-east-1 \
--nodegroup-name ram-nodes \
--node-type t3.medium \
--nodes 2 \
--nodes-min 1 \
--nodes-max 3 \
--managed


—---------------------------
Next Important Step: Enable EBS CSI driver for statefulset.yaml
eksctl create addon \
  --name aws-ebs-csi-driver \
  --cluster ram-eks \
  --region us-east-1 \
  --force

—-----------

eksctl utils associate-iam-oidc-provider --cluster ram-eks --approve

eksctl create iamserviceaccount \
  --name ebs-csi-controller-sa \
  --namespace kube-system \
  --cluster ram-eks \
  --role-name AmazonEKS_EBS_CSI_DriverRole \
  --attach-policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy \
  --approve


—-------------------------

eksctl create addon --name aws-ebs-csi-driver --cluster ram-eks --service-account-role-arn arn:aws:iam::<ACCOUNT_ID>:role/AmazonEKS_EBS_CSI_DriverRole --force



—---------------

kubectl describe pvc data-catalog-mysql-0 -n catalog

—--------------------


aws eks describe-nodegroup \
  --cluster-name ram-eks \
  --nodegroup-name ram-nodes \
  --region us-east-1 \
  --query "nodegroup.nodeRole" \
  --output text

—------- What You Need To Do:
Go to the AWS Console → IAM section → and follow these steps:

✅ Steps to Fix the EBS CSI 403 Error:
Open IAM Console:
 🔗 https://console.aws.amazon.com/iamv2/home#/roles


Search for this role:

 CopyEdit
eksctl-ram-eks-nodegroup-ram-nodes-NodeInstanceRole-x50UcEP1AC4F


Click on that Role


Select Attach policies


✅ In the search bar, type:

 nginx
CopyEdit
AmazonEBSCSIDriverPolicy


Check the box and click Attach policy
—--------------------


----------or -----------------

eksctl create cluster \
  --name petclinic-cluster \
  --region us-east-1 \
  --version 1.28 \
  --nodegroup-name petclinic-nodes \
  --node-type t3.medium \
  --nodes 2 \
  --nodes-min 1 \
  --nodes-max 3 \
  --managed \
  --vpc-public-subnets=subnet-035db96afc22fb36e \
  --vpc-id vpc-0e90a0345c59b32d3 \
  --node-volume-size 20 \
  --with-oidc \
  --ssh-access \
  --ssh-public-key Qalb_Key \
  --asg-access \
  --external-dns-access \
  --full-ecr-access \
  --alb-ingress-access \
  --node-ami auto \
  --tags project=petclinic,env=dev


kubectl get nodes


kubectl get nodes
kubectl get svc


kubectl create namespace petclinic

Step 4: Deploy PetClinic App to EKS
Use your deployment.yaml and service.yaml files.
spring-petclinic/
└── k8s/
    ├── deployment.yaml        # App deployment
    ├── service.yaml           # App service
    ├── db.yml                 # DB setup (e.g., MySQL/Postgres)
    └── namespace.yaml   
Step into the k8s folder
cd spring-petclinic/k8s
kubectl apply -f k8s/deployment.yaml -n petclinic
kubectl apply -f deployment.yaml -n petclinic
kubectl apply -f k8s/service.yaml -n petclinic
kubectl apply -f service.yaml -n petclinic

kubectl get pods -n petclinic

LoadBalancer URL

kubectl get svc spring-petclinic-service -n petclinic



http://<EXTERNAL-IP>


kubectl logs -n petclinic spring-petclinic-6858649885-jgwrw


kubectl logs -f -n petclinic spring-petclinic-6858649885-jgwrw

k8skubectl top pod -n petclinicic
NAME                                CPU(cores)   MEMORY(bytes)
spring-petclinic-6858649885-jgwrw   2m           255Mi

watch kubectl get all -n petclinic
Delete cluster 
eksctl delete cluster --name ram-eks --region us-east-1


Docker compose install 

sudo apt update
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64 \
  -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose

mkdir prometheus-grafana
cd prometheus-grafana


Vi prometheus.yml

# prometheus.yml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']


Vi docker-compose.yml 
version: '3'

services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana:latest
    container_name: grafana
    ports:
      - "3000:3000"

docker compose up -d

Prometheus → http://localhost:9090


Grafana → http://localhost:3000



Prometheus + Grafana
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

helm version


helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

kubectl create namespace monitoring

helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring

kubectl get pods -n monitoring

kubectl port-forward -n monitoring svc/kube-prometheus-stack-grafana 3000:80

kubectl get secret -n monitoring kube-prometheus-stack-grafana -o jsonpath="{.data.admin-password}" | base64 --decode

kubectl patch svc kube-prometheus-stack-grafana -n monitoring -p '{"spec": {"type": "LoadBalancer"}}'

kubectl get svc -n monitoring kube-prometheus-stack-grafana

Open the browser:

 cpp
CopyEdit
http://<your-external-ip>

Login:


Username: admin


Password: Run:


kubectl get secret -n monitoring kube-prometheus-stack-grafana -o jsonpath="{.data.admin-password}" | base64 --d

prom-operator



kubectl create namespace monitoring

helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring

kubectl get pods -n monitoring

kubectl port-forward -n monitoring svc/kube-prometheus-stack-grafana 3000:80

kubectl get secret -n monitoring kube-prometheus-stack-grafana -o jsonpath="{.data.admin-password}" | base64 --decode




Final Check
 Jenkins  –   ci/cd
 Checkout code -git
 Code Build & Test  - maven
 Sonar scan - maven
 Build Docker image -docker
 Push to Docker Hub -dockerhub
 Infrastructure -aws-cli ,cloudformation
 Deploy to EKS 








   







