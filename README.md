# 🚀 Two-Tier Flask App Deployment

🔗 [LinkedIn – Deepak Patel](https://www.linkedin.com/in/deepakpatel02/)

## 📌 Project Architecture
---![TwoTierFlaskAppFinal](https://github.com/user-attachments/assets/2acfbb5b-0a9c-40bb-a758-af0eb4d128c0)

---
## 📌 Project documentation link

---

## 📄 Project Description

This project demonstrates the implementation of a CI/CD pipeline for deploying a two-tier Flask web application. The process is fully automated using Jenkins and Docker, with security checks integrated via Trivy. The pipeline follows best DevOps practices, including:

- Developers push code to GitHub.
- Jenkins Master on EC2 triggers the pipeline and delegates tasks to Jenkins Agent.
- Jenkins Agent performs a file system vulnerability scan using Trivy.
- Docker image is built, tested, and pushed to Docker Hub.
- The latest Docker image is deployed using Docker Compose.

This setup ensures continuous integration, continuous delivery, and security throughout the software delivery lifecycle.

---

## 🛠️ Tools & Technologies

- **Jenkins** – CI/CD automation server (master/agent setup)
- **Trivy** – Vulnerability scanner for secure builds
- **Docker** – Containerization of the application
- **Docker Hub** – Container registry for image storage
- **GitHub** – Source code repository
- **EC2 (AWS)** – Hosting Jenkins master and agent nodes

---

## 🔄 Project Workflow

### Step 1: Create EC2 Instances  
Create **2 EC2 instances** – one for Jenkins master, one for Jenkins agent.

---

### Step 2: Setup Jenkins Master Node  
Install Jenkins, configure firewall, plugins, and create initial admin credentials.

---

### Step 3: Setup Jenkins Agent Node  
Connect agent node using SSH credentials or a static agent configuration to perform pipeline tasks.

---

### Step 4: Create Jenkins Job  
- Create a new pipeline job.
- Add your Jenkinsfile to the job (from SCM or inline).

---

### Step 5: Generate Docker Hub PAT  
- Login to [Docker Hub](https://hub.docker.com).
- Generate a **Personal Access Token** to push images securely.

---

### Step 6: Add Credentials to Jenkins  
- Go to:Jenkins → Manage Jenkins → Credentials → Global → Add Credentials
- Add DockerHub username and PAT.

---

### Step 7: Build the Pipeline  
- Trigger the pipeline manually.
- Observe stages: clone, scan, build, push, deploy.

---

### Step 8: Check Container Status  
Use `docker ps` on your Jenkins agent to confirm containers are up and running.

---

### Step 9: Open Flask App in Browser  
- Allow **port 5000** in your EC2 security group.
- Access your Flask app using:  
  `http://<EC2_PUBLIC_IP>:5000`

---

### Step 10: Add GitHub Webhook  
Set up webhook in GitHub to automatically trigger the pipeline on push.

---

### Step 11: Use Script from SCM  
Link your GitHub repo in the pipeline job to use the Jenkinsfile directly from source control.

---

### Step 12: Install Trivy  
Install Trivy on the Jenkins agent to perform file system vulnerability scans.

---

### Step 13: Jenkinsfile Testing  
Make code changes and push to GitHub to validate the pipeline re-runs and reflects updates.

---

## ✅ Conclusion

This project showcases a practical DevOps workflow to deploy secure and scalable Flask applications. By integrating **Trivy** into the CI/CD pipeline, it ensures that **security scanning is automated** before deployment. The **Jenkins master-agent** model allows efficient build orchestration, and **Docker** simplifies application packaging and delivery. This architecture is ideal for **small to medium-scale deployments** with strong automation needs.

---

🔧 Happy Learning!

