# 🚀 DevOps Driven Cloud Deployment Monitoring

A cloud-native DevOps project that integrates CI/CD automation, containerization, and robust cloud monitoring using industry-standard tools and platforms.

## 🧰 Tech Stack Badges

<p align="center">
  <img src="https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white" alt="Git"/>
  <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub"/>
  <img src="https://img.shields.io/badge/Jenkins-D24939?logo=jenkins&logoColor=white" alt="Jenkins"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white" alt="Docker"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white" alt="Prometheus"/>
  <img src="https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white" alt="Grafana"/>
  <img src="https://img.shields.io/badge/AWS-FF9900?logo=amazonaws&logoColor=white" alt="AWS"/>
</p>

## ✅ Why These Tools?

- **Git** – Tracks and manages source code changes with version control.
- **GitHub** – Hosts code with collaboration, issue tracking, and GitHub Actions.
- **Jenkins** – Automates CI/CD pipelines for building, testing, and deploying applications.
- **Docker** – Packages applications into portable, consistent containers.
- **Prometheus** – Collects real-time metrics and triggers alerts for infrastructure health.
- **Grafana** – Visualizes metrics with rich dashboards and monitoring panels.
- **AWS** – Provides scalable, secure cloud infrastructure for deployment and monitoring.

## 🖥️ Infrastructure Setup

The project runs on a single **AWS EC2 Ubuntu instance** with the following DevOps tools installed:

- Jenkins (CI/CD)
- Docker (Containerization)
- Prometheus (Monitoring)
- Grafana (Dashboard Visualization)

## 🔁 Project Workflow

The pipeline follows a fully automated DevOps lifecycle — from code commit to cloud deployment and monitoring.

---

### 🧩 Step-by-Step Breakdown

🔹 **1. Checkout Code from GitHub**  
➡️ Jenkins automatically pulls the latest code from the GitHub repository when changes are pushed.

🔹 **2. Build Docker Image**  
➡️ Jenkins builds a Docker image from the `Dockerfile`, packaging the application and its dependencies.

🔹 **3. Push to Docker Hub**  
➡️ The image is tagged and pushed to a public/private Docker Hub registry.

🔹 **4. Run Docker Compose**  
➡️ Jenkins executes `docker-compose up` to deploy the container(s) on the EC2 instance.

🔹 **5. Prometheus Scrapes Metrics**  
➡️ Prometheus collects real-time metrics from the container’s `/metrics` endpoint (if exposed), or using a Node Exporter for system metrics.

🔹 **6. Grafana Visualizes Everything**  
➡️ Grafana queries Prometheus and presents **CPU**, **RAM**, **network**, and custom app metrics in rich, real-time dashboards.

---

🎯 **Result:**  
A continuously deployed, containerized app with full-stack observability — all running on a single AWS EC2 instance.
