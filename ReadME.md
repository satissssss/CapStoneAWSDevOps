1. Created new git repo and pushed the code to the repo.
Repo URL - https://github.com/satissssss/CapStoneAWSDevOps

2. Setup Softwares for CICD pipelines setup
--Install jenkins
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

-- Install Java
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
openjdk version "21.0.3" 2024-04-16
OpenJDK Runtime Environment (build 21.0.3+11-Debian-2)
OpenJDK 64-Bit Server VM (build 21.0.3+11-Debian-2, mixed mode, sharing)

--Start installed jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status Jenkins

--Get password after install from to setup new admin user
 /var/lib/jenkins/secrets/initialAdminPassword

Access the Jenkins on Public DNS on port 8080

--Setup AWS credential in the Manage Jenkins --> Global Credentials

3. Setup K8s and EKS
Setup EKS and K8s through Jenkins with K8sEKSJenkinsfile on repo

4. Setup Apps
Push image to Docker through Jenkins with DockerhubJenkinsfile on repo
Setup Apps and run through jenkins with AppDeployJenkinsfile on repo

5. Setup different pipeline for development and production env with different branch for each:
Create separate branch as dev and use main as production in github

Setup namespace for development and productiona and deploy Apps
Create namespace:
kubectl apply -f namespace_dev.yaml
kubectl apply -f namespace_prod.yaml

Deploy app into namespace by adding --namespace at end
kubectl apply -f kubernetes.yaml --namespace=development
kubectl apply -f kubernetes.yaml --namespace=production

Check deployed pods in namespace:
kubectl get pods --namespace=development

6. Delete the EKS cluster using pipeline
Setup EKS and K8s through Jenkins with K8sEKSdeleteJenkinsfile on repo


