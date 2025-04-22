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

### 🔧 Installation Script for Ubuntu EC2

Use the following bash script to install all required tools on your Ubuntu-based EC2 instance:

```bash
#!/bin/bash

# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Docker
sudo apt install -y docker.io
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker ubuntu  # or $(whoami)

# Install Jenkins
sudo apt install -y openjdk-11-jdk
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install -y jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins

# Install Prometheus
wget https://github.com/prometheus/prometheus/releases/download/v2.48.1/prometheus-2.48.1.linux-amd64.tar.gz
tar xvf prometheus-*.tar.gz
sudo mv prometheus-*/prometheus /usr/local/bin/
sudo mv prometheus-*/promtool /usr/local/bin/

# Create Prometheus config and service
sudo useradd --no-create-home --shell /bin/false prometheus
sudo mkdir -p /etc/prometheus /var/lib/prometheus
sudo chown prometheus:prometheus /etc/prometheus /var/lib/prometheus

cat <<EOF | sudo tee /etc/systemd/system/prometheus.service
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/var/lib/prometheus/

[Install]
WantedBy=default.target
EOF

sudo systemctl daemon-reexec
sudo systemctl start prometheus
sudo systemctl enable prometheus

# Install Grafana
sudo apt install -y apt-transport-https software-properties-common
sudo wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt update
sudo apt install -y grafana
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
