# 🌥️ Staging Environment – URL Shortener Application

The **Staging Environment** serves as a pre-production testing layer where new features, configurations, and infrastructure changes are validated before reaching production.

This environment is deployed **manually using Helm charts** onto an **Amazon EKS cluster**.

![Animation](https://github.com/user-attachments/assets/f99e65bb-7d19-43a8-a0a1-b57686d16ef5)

---

## 🛠 Staging Tech Stack

### Infrastructure
- **AWS EKS**
- **Helm Charts**
- **Amazon ECR (pulling pre-built images)**
- **EC2 Worker Nodes**

### Monitoring
- **Prometheus**
- **Grafana Dashboards**
- **AlertManager** (testing alerts before production)

### Deployment
- **Manual Helm Installation**
- **Helm Upgrade for updates**
- **Separate values.yaml for staging**

---

## 🧩 Architecture Overview

The staging environment mirrors production but operates independently to allow safe testing.

Key components:
- **Backend API (Flask)**
- **Frontend (React/Vite)**
- **Monitoring Stack (Prometheus + Grafana + Alerts)**
- **Ingress Controller**
- **Persistent Volumes for monitoring components**

---

## 🚀 Deployment Workflow (Manual Helm)

### 1️⃣ Connect to EKS Cluster
```bash
aws eks update-kubeconfig --region <region> --name <EKS_CLUSTER_NAME>
```

### 2️⃣ Ensure Namespace Exists
```bash
Copy code
kubectl create namespace url-shortener-staging
```

### 3️⃣ Deploy Using Helm
```bash
Copy code
helm install url-shortener-staging ./helm \
  -f ./helm/values-staging.yaml \
  -n url-shortener-staging
```

### 4️⃣ Upgrade Deployment (when needed)
```bash
Copy code
helm upgrade url-shortener-staging ./helm \
  -f ./helm/values-staging.yaml \
  -n url-shortener-staging
```

### 5️⃣ Validate Resources
```bash
Copy code
kubectl get all -n url-shortener-staging
```


Upgrade Deployment (when needed)
```bash
helm upgrade url-shortener-staging ./helm \
  -f ./helm/values-staging.yaml \
  -n url-shortener-staging
```


## Screenshots 📸

### Dockerizing images and push it to ECR Private Repos
<img width="1892" height="861" alt="Screenshot 2025-12-05 001937" src="https://github.com/user-attachments/assets/3f66dd3f-fa8e-4343-9861-62ba1ab4ea73" />
<img width="1899" height="871" alt="Screenshot 2025-12-05 002003" src="https://github.com/user-attachments/assets/64832cc5-8519-433f-96d2-fbda37cc1f60" />


### End-to-End CI/CD Pipeline 
<img width="1889" height="545" alt="Screenshot 2025-12-08 161231" src="https://github.com/user-attachments/assets/ec28cb6f-550e-4cce-b4f9-a0b65e5d8349" />
<img width="1911" height="603" alt="Screenshot 2025-12-08 161206" src="https://github.com/user-attachments/assets/c7a09ccf-09b8-4d8e-ab7f-9e6099233a8a" />
<img width="1077" height="857" alt="Screenshot 2025-12-08 161308" src="https://github.com/user-attachments/assets/198a0064-b8a7-4793-acaa-959b953c3bec" />

### Deploy using Helm in Pipeline
<img width="1919" height="932" alt="Screenshot 2025-12-06 192452" src="https://github.com/user-attachments/assets/5158d492-5f85-4892-a5ef-9741b56e37f2" />
<img width="1087" height="844" alt="Screenshot 2025-12-08 161500" src="https://github.com/user-attachments/assets/303db3ea-4f6b-46f9-a836-a12c00279071" />

### Resources in staging namespaces
<img width="1919" height="266" alt="Screenshot 2025-12-08 154939" src="https://github.com/user-attachments/assets/391b4291-1a6f-42d1-b1ab-34e170047ecb" />
<img width="756" height="567" alt="Screenshot 2025-12-08 155003" src="https://github.com/user-attachments/assets/c4c57c71-612b-487c-bae4-e5d1cd97f0b0" />

### Exposing Frontend svc for testing
<img width="841" height="158" alt="Screenshot 2025-12-08 155247" src="https://github.com/user-attachments/assets/39d3fc79-8843-47ac-8910-78667c16c59a" />
<img width="1466" height="998" alt="Screenshot 2025-12-08 155759" src="https://github.com/user-attachments/assets/3b0824a0-3685-4931-b67c-fe644ca77e29" />


