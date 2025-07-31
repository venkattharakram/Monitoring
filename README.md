Monitor Kubernetes Cluster using Prometheus and Grafana | Kubernetes Cluster Monitoring

🐳 Docker Installation
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y

docker --version
docker compose version


⚙️ Kubectl CLI Installation
sudo apt update
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version --client


🌱 Minikube Installation
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl apt-transport-https ca-certificates conntrack
wget -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version
minikube start


📦 Add Helm Repositories
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

Create Namespace
kubectl create namespace prometheus

🛠️ Install Prometheus
helm install prometheus prometheus-community/prometheus --namespace prometheus

<img width="1920" height="1080" alt="Screenshot from 2025-07-31 21-40-41" src="https://github.com/user-attachments/assets/beff42ec-03a7-4e7b-a329-53cb9aa28714" />


Create Namespace
kubectl create namespace grafana

📊 Install Grafana
helm install grafana grafana/grafana --namespace monitoring

<img width="1920" height="1080" alt="Screenshot from 2025-07-31 21-39-57" src="https://github.com/user-attachments/assets/df5f9fb2-a966-4eb6-ad44-2f800dcc3f56" />


🔗 Add Prometheus as a Grafana Data Source
Open Grafana UI
Go to Settings → Data Sources

Click Add Data Source

Select Prometheus

URL: http://192.168.49.2:30567


Click Save & Test

📈 Import Dashboards
Go to Dashboard → Import

Use popular dashboard IDs (e.g., 315, 186


📉 Minikube Cluster Dashboard
![Uploading Screenshot from 2025-07-31 21-43-12.png…]()





