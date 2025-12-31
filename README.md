# 🚀 CI/CD Pipeline with Jenkins, Ansible, Docker & GitHub Webhooks on AWS

## 📌 Project Overview

This project demonstrates how to build a **fully automated CI/CD (Continuous Integration & Continuous Deployment) pipeline** using **Jenkins, Ansible, Docker, and GitHub Webhooks**, all deployed on **Amazon Web Services (AWS)**.

The goal of this project is to automate the complete software delivery lifecycle — from code commit to deployment — using modern DevOps tools and best practices. This setup is ideal for **DevOps beginners, cloud engineers, and students** looking to strengthen their hands-on experience and enhance their resumes.

---

## 🧰 Tools & Technologies Used

* **AWS EC2** – Cloud infrastructure to host Jenkins, Ansible, and Docker
* **Jenkins** – Automation server for CI/CD pipelines
* **Ansible** – Configuration management and deployment automation
* **Docker** – Containerization of applications
* **GitHub** – Source code management
* **GitHub Webhooks** – Automatic pipeline trigger on code push
* **Linux (Ubuntu)** – Operating system for servers

---

## 🏗️ Architecture Overview

1. Developer pushes code to **GitHub repository**
2. **GitHub Webhook** triggers Jenkins automatically
3. **Jenkins** pulls the latest code from GitHub
4. Jenkins executes **Ansible playbooks**
5. **Ansible**:

   * Copies application files to target server
   * Builds Docker image
   * Runs Docker container
6. Application is deployed successfully 🚀

---

## 📂 Project Structure

```
ansible-jenkins-pipeline/
│
├── Dockerfile
├── deployment.yaml
├── inventory.ini
├── Jenkinsfile
├── app/
│   └── (application source code)
└── README.md
```

---

## ⚙️ Prerequisites

Before starting, ensure you have:

* AWS account
* EC2 instances (Ubuntu)
* Jenkins installed and running
* Ansible installed on Jenkins server
* Docker installed on target server
* GitHub account & repository
* SSH key-based authentication configured

---

## 🔧 Jenkins Setup

1. Install Jenkins on AWS EC2
2. Install required plugins:

   * Git
   * GitHub Integration
   * Ansible
3. Configure Jenkins credentials:

   * GitHub credentials
   * SSH private key for Ansible
4. Create a Jenkins job or pipeline

---

## 🔗 GitHub Webhook Configuration

1. Go to your GitHub repository
2. Navigate to **Settings → Webhooks**
3. Add webhook URL:

   ```
   http://<JENKINS_PUBLIC_IP>:8080/github-webhook/
   ```
4. Select **Just the push event**
5. Save webhook

Now every code push will automatically trigger Jenkins 🎯

---

## 📦 Ansible Deployment

Ansible is used to automate:

* File transfer
* Docker image build
* Docker container deployment

### Sample Playbook

```yaml
- name: Build & deploy docker container
  hosts: dockerserver
  become: true
  remote_user: ubuntu

  tasks:
    - name: Build Docker image
      docker_image:
        name: myapp:latest
        build:
          path: /home/ubuntu/projects
        state: present

    - name: Run Docker container
      docker_container:
        name: myapp-container
        image: myapp:latest
        ports:
          - "80:80"
        state: started
```

---

## 🐳 Docker Integration

* Application is containerized using Docker
* Dockerfile defines application environment
* Containers ensure portability and scalability

---

## ☁️ AWS Benefits

* Scalable infrastructure
* High availability
* Secure cloud environment
* Easy integration with DevOps tools

---

## 🎯 Key Learning Outcomes

* Hands-on CI/CD pipeline implementation
* Jenkins automation with GitHub Webhooks
* Ansible-based deployment automation
* Docker containerization
* AWS cloud infrastructure usage
* Real-world DevOps workflow

---

## 📈 Use Cases

* Resume-ready DevOps project
* Real-time CI/CD automation demo
* Learning DevOps tools integration
* Small to medium production pipelines

---

## 🤝 Contribution

Feel free to fork this repository, improve the pipeline, or add new features. Pull requests are welcome!

---

## 📜 License

This project is open-source and available for educational purposes.

---

## ⭐ Support

If you found this project helpful, don’t forget to ⭐ star the repository and share it with others!

Happy DevOps! 🚀
