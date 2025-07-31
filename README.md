# 📊 Monitor Kubernetes Cluster using Prometheus and Grafana  
### Kubernetes Cluster Monitoring Guide

---

## 🐳 Docker Installation

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y

docker --version
docker compose version
```

---

## ⚙️ Kubectl CLI Installation

```bash
sudo apt update
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client
```

---

## 🌱 Minikube Installation

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl apt-transport-https ca-certificates conntrack
wget -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube version
minikube start
```

---

## 📦 Add Helm Repositories

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

---

## 🛠️ Install Prometheus

Create a namespace for Prometheus:

```bash
kubectl create namespace prometheus
```

Install Prometheus:

```bash
helm install prometheus prometheus-community/prometheus --namespace prometheus
```

<img width="1920" height="1080" alt="Screenshot from 2025-07-31 23-18-18" src="https://github.com/user-attachments/assets/f695fe54-bf26-4284-b789-96d2d49567c5" />

---

## 📊 Install Grafana

Create a namespace for Grafana:

```bash
kubectl create namespace grafana
```

Install Grafana:

```bash
helm install grafana grafana/grafana --namespace grafana
```

<img width="1920" height="1080" alt="Screenshot from 2025-07-31 23-17-29" src="https://github.com/user-attachments/assets/a8d99585-c0ca-4cc2-8cec-ebed441314f5" />

---

## 🔗 Add Prometheus as a Grafana Data Source

1. Open Grafana UI.
2. Go to **Settings → Data Sources**.
3. Click **Add Data Source**.
4. Select **Prometheus**.
5. Set the URL:

   ```
   http://192.168.49.2:30567
   ```

6. Click **Save & Test**.

---

## 📈 Import Dashboards

1. Go to **Dashboard → Import**.
2. Use popular dashboard IDs, for example:
   - `315`
   - `1860`

---

## 📉 Minikube Cluster Dashboard

<img width="1920" height="1080" alt="Screenshot from 2025-07-31 23-16-08" src="https://github.com/user-attachments/assets/2a248254-1423-4bc1-8099-1670285ac7b5" />
