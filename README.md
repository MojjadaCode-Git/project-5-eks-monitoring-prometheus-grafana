# Project-5-Monitoring-
Project-5-Monitoring


📊 Project 5 – Monitoring AWS EKS using Prometheus & Grafana
🔥 Project Overview

This project demonstrates how to implement monitoring and observability for a Kubernetes cluster running on AWS EKS using Prometheus for metrics collection and Grafana for visualization.

The monitoring stack collects metrics from cluster nodes, pods, and Kubernetes components and visualizes them through real-time dashboards.

#############################################################

## Known Limitation
- Prometheus Alertmanager pod is in Pending state due to lack of persistent storage (PVC).
- This does not impact Prometheus metric collection or Grafana dashboards.
- For production, Alertmanager would be backed by EBS/EFS storage.

################################################################

🎯 Objectives

Create an AWS EKS cluster with managed node groups

Install Prometheus to collect Kubernetes and node metrics

Install Grafana to visualize metrics using dashboards

Expose Grafana using AWS LoadBalancer

Monitor CPU, memory, pods, and node health

🛠️ Tools & Technologies Used

AWS EKS

Kubernetes

eksctl

kubectl

Helm

Prometheus

Grafana

AWS Elastic Load Balancer (ELB)

🏗️ Architecture
User Browser
     |
     v
AWS Load Balancer (Grafana)
     |
     v
Grafana Dashboard
     |
     v
Prometheus Server
     |
     v
Kubernetes Cluster (EKS)
 ├── Worker Nodes
 ├── Pods
 ├── Node Exporter
 └── kube-state-metrics

 #####################################################

 🚀 Implementation Steps
1️⃣ Create EKS Cluster
eksctl create cluster \
  --name monitoring-cluster \
  --region us-east-1 \
  --nodegroup-name workers \
  --node-type t3.medium \
  --nodes 2

####################################################

  Verify Cluster & Nodes
eksctl get cluster --region us-east-1
kubectl get nodes
kubectl get pods -n kube-system

#####################################################

Verify Cluster & Nodes
eksctl get cluster --region us-east-1
kubectl get nodes
kubectl get pods -n kube-system

######################################################

3️⃣ Install Helm
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
helm version

#######################################################

4️⃣Add Helm Repositories
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

#######################################################

5️⃣ Create Monitoring Namespace
kubectl create namespace monitoring

#######################################################

8️⃣ Expose Grafana using LoadBalancer
kubectl expose deployment grafana \
  --type=LoadBalancer \
  --name=grafana-service \
  --port=3000 \
  --target-port=3000 \
  -n monitoring

  
