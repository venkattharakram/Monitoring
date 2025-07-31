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

![Screenshot from 2025-07-31 21-40-41](#)

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

![Screenshot from 2025-07-31 21-39-57](#)

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

![Screenshot from 2025-07-31 21-43-12](#)
