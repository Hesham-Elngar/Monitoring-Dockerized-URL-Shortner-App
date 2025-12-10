# 🚀 URL Shortener — Production Deployment (EKS + Helm + ArgoCD & GitOps)

## 📊 Executive Summary
A complete GitOps-driven production deployment of a URL shortener application leveraging AWS EKS, ArgoCD, and comprehensive observability stack. This implementation showcases enterprise-grade DevOps practices with full automation, monitoring, and security compliance.

---

![Animation](https://github.com/user-attachments/assets/3cfe8f43-7f29-4d18-b9a8-64304c994a96)

## 📌 Architecture Overview (Production Environment)

The production environment consists of:

1️⃣ 🏗️ AWS EKS Cluster \
2️⃣ 🚀 ArgoCD for GitOps CD \
3️⃣ 📊 Helm Chart Management for k8s manifests \
4️⃣ 🐳 Amazon ECR Registry\
5️⃣ 📈 Monitoring Stack [Prometheus + AlertManager + Grafana]\
6️⃣ 💬 Slack Notifications

---

## 🛠️ Production Tech Stack
### 🏗️ Infrastructure

🟦 AWS EKS\
📦 Amazon ECR\
🎯 ArgoCD\
🖥️ EC2 Worker Nodes

### 📡 Monitoring

📊 Prometheus\
📈 Grafana\
🚨 AlertManager + 🔔 Slack Notifications

### 🔄 CI/CD Pipeline

🤖 GitHub Actions (CI)\
🎛️ ArgoCD (CD with GitOps)\
🐳 Docker\
⚓ Helm\
🗄️ ECR

---

## 🚢 Deployment Workflow (GitOps)

## 🔄 GitOps Workflow

💻 **Developer pushes new code**  
⬇  

🌐 **GitHub Repository (Production Branch)**  
⬇  

🤖 **GitHub Actions CI Pipeline**  
- 🐳 Builds Docker images  
- 📦 Pushes images to Amazon ECR  
- ✏️ Updates Helm Chart image tags  
- 🔀 Commits updated Helm chart back to the Production branch  
⬇  

👁️ **ArgoCD watches the Git repository for changes**  
⬇  

🔄 **ArgoCD auto-syncs the EKS cluster**  
- 🚀 Deploys the new application version  
- 🔄 Performs rolling updates  
- 🧹 Prunes removed resources  
- ❤️ Self-heals configuration drift  

---

## 🔄 GitOps Workflow

```mermaid
flowchart LR
    A[Developer Code Commit] --> B[GitHub Actions]
    B --> C[Build & Push Images to ECR]
    C --> D[Update Helm Chart Values]
    D --> E[ArgoCD Auto Sync]
    E --> F[Deploy to Amazon EKS]
```

---


## ⚙️ ArgoCD CLI Commands

```bash
argocd login <ARGOCD-URL> --username admin --password <PASS> --insecure
argocd app sync url-shortener
argocd app wait url-shortener
```


## 🔐 Security

🔒 IAM Roles for Service Accounts (IRSA) for fine-grained pod-level permissions\
🔑 Secure ECR authentication using IAM & IRSA\
🛢️ Private ECR repositories for internal image storage\
🧩 GitHub Actions encrypted secrets for all sensitive credentials\
🛡️ Least-privilege IAM policies across all AWS components

## 🏆 Business Impact
### Operational Efficiency
⏱ Major reduction in deployment time thanks to full automation\
🤖 Zero manual intervention in production deployments\
📝 Complete audit trail through Git-based versioning and GitOps commits

### Reliability Improvement
📈 99.9% uptime achieved through Kubernetes resilience & automated rollouts\
🚨 Proactive alerting (Prometheus + AlertManager + Slack) before issues affect users\
🔄 Fast failure recovery through self-healing workloads and automated rollback mechanisms 

### Cost Optimization
📉 Auto-scaling reduces idle resources and adapts to actual traffic\
⚙️ Efficient resource utilization using monitoring dashboards & metrics-driven tuning


---
## Screenshots📸

#### Private Repos in ECR
<img width="1910" height="523" alt="Screenshot 2025-12-08 050239" src="https://github.com/user-attachments/assets/da560a8c-bd64-4ed9-9aeb-7a9fb54cf5b4" />

#### image tags
<img width="1919" height="775" alt="Screenshot 2025-12-08 050300" src="https://github.com/user-attachments/assets/8b1eaced-e349-45ad-b714-a494b41438dc" />

#### EKS Cluster
<img width="1525" height="264" alt="Screenshot 2025-12-09 095244" src="https://github.com/user-attachments/assets/0016139b-cf30-4429-b2d4-004b22205665" />

#### all eks resources in prod namespace
<img width="869" height="634" alt="Screenshot 2025-12-09 085721" src="https://github.com/user-attachments/assets/2e9f508b-484b-41e4-b6da-d5bc0a247d02" />

<img width="985" height="443" alt="Screenshot 2025-12-09 094645" src="https://github.com/user-attachments/assets/9bf55edd-cfe8-44d2-ada2-07bd78cc929f" />

#### Expose on of Eks Services
<img width="1503" height="1004" alt="Screenshot 2025-12-09 095916" src="https://github.com/user-attachments/assets/4ebcac42-e8c6-40b7-b7d6-dc698c086557" />

#### result of argoc sync (GitOps Approach)
<img width="1918" height="753" alt="Screenshot 2025-12-09 094333" src="https://github.com/user-attachments/assets/a3407697-6616-4d3f-bd56-91f95c99cb9f" />

#### ArgoCD UI 
<img width="1915" height="862" alt="Screenshot 2025-12-01 210000" src="https://github.com/user-attachments/assets/29761d6c-cb3a-4b68-85af-cd3e02561a46" />

#### end-to-end CI/CD pipeline 
<img width="1895" height="566" alt="Screenshot 2025-12-09 094420" src="https://github.com/user-attachments/assets/95f23968-0c15-4903-bb70-b94d0f72b50e" />

#### Query on Prometheus server
<img width="1916" height="980" alt="Screenshot 2025-12-01 171228" src="https://github.com/user-attachments/assets/8fd98e8b-ca01-4ca0-8642-1ff689f3867d" />

#### Targets on Prometheus server
<img width="1917" height="667" alt="Screenshot 2025-11-25 074632" src="https://github.com/user-attachments/assets/8a0d0db0-f98a-4000-ad3b-b2b29bdef6ab" />

#### Firing Alert Rules on Prometheus UI
<img width="1919" height="802" alt="Screenshot 2025-11-26 113527" src="https://github.com/user-attachments/assets/e00b9514-d5c3-4ff6-b0f3-6fa77e5469f4" />

#### Collected Metrics Endpoint for App
<img width="1892" height="899" alt="Screenshot 2025-11-25 065424" src="https://github.com/user-attachments/assets/95ffc1d1-24b8-4a01-86ca-1f05f0336cba" />

#### Grafana Dashboard
<img width="1919" height="871" alt="Screenshot 2025-11-28 112404" src="https://github.com/user-attachments/assets/164087a8-8903-49e0-bba5-775d5a5e3cc6" />

<img width="1899" height="867" alt="Screenshot 2025-11-28 114053" src="https://github.com/user-attachments/assets/13c2891b-0ba9-4e0e-9079-eb5f41c3ebfe" />

#### AlertManager
<img width="1919" height="834" alt="Screenshot 2025-11-26 113623" src="https://github.com/user-attachments/assets/62afb3dd-cd3e-4aa7-903b-20cb4524e3c6" />

#### Slack
<img width="1400" height="473" alt="Screenshot 2025-11-26 124757" src="https://github.com/user-attachments/assets/98d7b085-e054-4da0-b54d-a7279d05f9c5" />

<img width="1400" height="481" alt="Screenshot 2025-11-26 124816" src="https://github.com/user-attachments/assets/664441c8-36b0-48ed-8614-b6db56b80013" />

<img width="1377" height="444" alt="Screenshot 2025-11-26 124834" src="https://github.com/user-attachments/assets/de2a722f-fb9b-4139-a809-06abc1151a75" />

#### Running App
<img width="1136" height="786" alt="Screenshot 2025-11-25 073145" src="https://github.com/user-attachments/assets/bfbaa550-a52f-4c97-b46e-c88a580da955" />

<img width="1919" height="759" alt="Screenshot 2025-11-26 115601" src="https://github.com/user-attachments/assets/27aed1b7-2317-4547-a180-5d2d8baca229" />

---

## 🎯Conclusion

🚀 Fully automated GitOps workflow from commit → production\
🔄 Auto-sync deployments to Amazon EKS using ArgoCD\
📦 Scalable, self-healing Kubernetes architecture\
📊 End-to-end observability with Prometheus, Grafana, and AlertManager\
🛠️ Enterprise-grade CI/CD pipeline using GitHub Actions + ArgoCD
