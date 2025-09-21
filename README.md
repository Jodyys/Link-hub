# LinkHub — Panduan Utama

Repo ini berisi desain infrastruktur dan contoh Helm Chart untuk aplikasi **LinkHub**.

---

## Desain Infrastruktur Singkat

* **Kubernetes** sebagai platform orkestrasi.
* **Ingress Controller (NGINX/Traefik)** untuk routing HTTP/HTTPS.
* **Frontend (React.js)** untuk antarmuka pengguna.
* **Backend (Go API)** untuk logika bisnis.
* **PostgreSQL** sebagai database.
* **Observability**: Prometheus, Grafana, Loki.
* **Security**: cert-manager, SealedSecrets, OPA, Trivy.

Topologi umum:
**User → Load Balancer → Ingress → Frontend/Backend → Database**

---

## Helm Chart Backend

Tersedia di folder `linkhub-backend/`.

* **Chart.yaml** → metadata chart.
* **values.yaml** → konfigurasi default (image, service, probes, db).
* **templates/** → Deployment, Service, Ingress, ConfigMap.

Fitur utama:

* Liveness & Readiness Probes.
* Resource Requests & Limits.
* Konfigurasi fleksibel via `values.yaml`.

---

## Cara Menggunakan Helm Chart

### 1. Install Chart

```bash
cd linkhub-backend/
helm install linkhub-backend . -f values.yaml
```

### 2. Update Chart

```bash
helm upgrade linkhub-backend . -f values.yaml
```

### 3. Uninstall Chart

```bash
helm uninstall linkhub-backend
```

---

📌 Dengan panduan ini, aplikasi LinkHub dapat dideploy di Kubernetes dengan mudah, aman, dan scalable.

