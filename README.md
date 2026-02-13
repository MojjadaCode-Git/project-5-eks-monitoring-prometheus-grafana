# Project 5 – EKS Monitoring with Prometheus & Grafana

## 📌 Objective
Deploy a monitoring solution for Amazon EKS using Prometheus and Grafana.

## 🛠 Tools Used
- AWS EKS
- eksctl
- Kubernetes
- Helm
- Prometheus
- Grafana

## 🏗 Architecture
- EKS Cluster with 2 worker nodes
- Prometheus for metrics collection
- Grafana for visualization

## 🚀 Steps
1. Create EKS cluster using eksctl
2. Install Prometheus via Helm
3. Install Grafana via Helm
4. Configure Prometheus as Grafana datasource
5. Import Kubernetes dashboards
6. Visualize CPU, Memory using gauges

## 📊 Dashboards
- Cluster Overview (ID: 315)
- Node Exporter Full (ID: 1860)
- Pod Monitoring (ID: 6417)

## 🧹 Cleanup
Run:
```bash
./cleanup/cleanup.sh
