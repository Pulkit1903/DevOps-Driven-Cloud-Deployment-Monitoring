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

This project automates the containerized deployment of an application, complete with monitoring using Prometheus and Grafana.

1. **Checkout Code from GitHub**  
   Jenkins pulls the latest code from the GitHub repository.

2. **Build Docker Image**  
   Jenkins uses the `Dockerfile` to build a Docker image for the application.

3. **Push to Docker Hub**  
   The built image is tagged and pushed to your Docker Hub repository.

4. **Run Docker Compose**  
   Jenkins triggers `docker-compose up` to deploy the containerized application.

5. **Prometheus Scrapes Metrics**  
   Prometheus is configured to scrape metrics from the running container (e.g., using `/metrics` endpoint).

6. **Grafana Visualizes Metrics**  
   Grafana connects to Prometheus as a data source and displays system-level metrics like **CPU usage**, **memory consumption**, etc., via prebuilt or custom dashboards.
