
# 📊 Kubernetes Monitoring Stack with Prometheus, Grafana, and Loki

This repository provides a fully automated setup to deploy a robust monitoring and logging stack on a Kubernetes cluster. The stack includes **Prometheus** for metrics, **Grafana** for visualization, **Loki** for log aggregation, and **Cert-Manager** for securing access using **Let's Encrypt** certificates. 

## 🚀 Features

- **Centralized Monitoring:** Collect and visualize metrics from Kubernetes and your applications using Prometheus and Grafana.
- **Centralized Logging:** Aggregate logs using Loki and view them through Grafana.
- **TLS Encryption:** Automatic SSL certificates with Let's Encrypt via Cert-Manager.
- **Automated Deployment:** Deploy everything via GitHub Actions.

---

## 📦 Components

1. **Prometheus:** Monitors the Kubernetes cluster and applications.
2. **Grafana:** Provides beautiful and customizable dashboards.
3. **Loki:** Collects and aggregates logs from Kubernetes pods.
4. **Promtail:** Sends logs to Loki.
5. **Cert-Manager:** Manages TLS certificates automatically.
6. **Ingress Controller:** Secure and route external access to Grafana and Loki.

---

## 🛠️ Prerequisites

- Kubernetes cluster (e.g., K3s, Minikube, EKS, GKE)
- `kubectl` configured to access your cluster
- GitHub Secrets configured:
  - `KUBE_CONFIG`: Base64-encoded kubeconfig file
  - `GRAFANA_ADMIN_PASSWORD`: Password for Grafana admin user
  - `CERT_MANAGER_EMAIL`: Email for Let's Encrypt notifications
  - `DOMAIN`: Domain where Grafana and Loki will be accessible

---

## 📝 How It Works

1. **Namespace Creation:** Creates the `monitoring` namespace.
2. **Deploy Prometheus:** Deploys Prometheus and its configuration.
3. **Deploy Grafana:** Deploys Grafana, configures datasources and ingress.
4. **Deploy Loki & Promtail:** Deploys Loki and its log collection agent.
5. **Setup TLS:** Configures Let's Encrypt certificates via Cert-Manager.
6. **Validation Steps:** Ensures all components are running correctly.

---

## 📂 File Structure

```
├── .github/workflows/deploy.yaml   # GitHub Actions CI/CD pipeline
├── namespace.yaml                  # Kubernetes namespace configuration
├── prometheus.yaml                 # Prometheus deployment and service
├── prometheus-config.yaml          # Prometheus scrape configurations
├── grafana.yaml                    # Grafana deployment and configuration
├── grafana-datasource.yaml         # Grafana datasource configuration
├── grafana-ingress.yaml            # Ingress for Grafana
├── loki.yaml                       # Loki deployment
├── promtail.yaml                   # Promtail deployment
├── loki-service.yaml               # Service for Loki
├── loki-ingress.yaml               # Ingress for Loki
├── letsencrypt-clusterissuer.yaml  # Let's Encrypt cluster issuer
├── grafana-certificate.yaml        # TLS certificate for Grafana
└── loki-certificate.yaml           # TLS certificate for Loki
```

---

## 🧑‍💻 How to Use

1. **Clone the Repository:**
```bash
git clone https://github.com/yourusername/monitoring-stack.git
cd monitoring-stack
```

2. **Configure Secrets:**
Add the following secrets to your GitHub repository:
- `KUBE_CONFIG`: Base64 kubeconfig file
- `GRAFANA_ADMIN_PASSWORD`: Password for Grafana
- `CERT_MANAGER_EMAIL`: Email for TLS certificates
- `DOMAIN`: Your root domain (e.g., `example.com`)

3. **Trigger Deployment:**
- Push changes to the `main` branch.
- The GitHub Action will automatically apply the manifests to your cluster.

4. **Verify Deployment:**
- Access Grafana at `https://grafana.yourdomain.com`
- Access Loki at `https://loki.yourdomain.com`

---

## 🔍 Troubleshooting

- **Check Pod Status:**  
```bash
kubectl get pods -n monitoring
```

- **View Logs:**  
```bash
kubectl logs -n monitoring <pod-name>
```

- **Check Ingress:**  
```bash
kubectl get ingress -n monitoring
```

---

## 📧 Support

If you encounter any issues, please open an issue on this repository or reach out to the maintainer.

---

## 🛡️ License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 🌟 Contributions

Contributions are welcome! Feel free to fork this repository, make changes, and submit pull requests.

Happy Monitoring! 🎯
