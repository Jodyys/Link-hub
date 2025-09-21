# TOOLING.md — Pilihan Tools Open Source untuk LinkHub

Dokumen ini menjelaskan daftar tools open-source yang dipilih untuk membangun infrastruktur aplikasi LinkHub di Kubernetes, beserta alasan pemilihannya.

---

## Orkestrasi & Networking

* **Kubernetes** → platform standar industri untuk orkestrasi kontainer, mendukung high availability, scalability, dan autoscaling.
* **Ingress-NGINX** (atau **Traefik**) → ingress controller open-source yang menangani routing HTTP/HTTPS dan TLS termination.
* **MetalLB** → load balancer untuk lingkungan bare-metal, agar service `type=LoadBalancer` tetap dapat digunakan.

## Database

* **PostgreSQL** → database relasional open-source yang kuat, cocok untuk menyimpan data pengguna dan link.
* **Zalando Postgres Operator** → memudahkan pengelolaan PostgreSQL dengan fitur HA (replication, failover otomatis).

## CI/CD & Deployment

* **Helm** → package manager Kubernetes untuk templating dan deployment aplikasi.
* **Argo CD** (atau **Flux**) → tool GitOps untuk sinkronisasi otomatis dari Git ke cluster Kubernetes.
* **Tekton Pipelines** → engine CI/CD berbasis Kubernetes untuk build, test, dan deploy aplikasi.

## Observability

* **Prometheus** → monitoring dan metrics collection (scrape `/metrics`).
* **Grafana** → visualisasi data dan alerting.
* **Loki** → sistem logging ringan yang terintegrasi dengan Grafana.
* **Jaeger** → distributed tracing untuk analisis performa request antar service.

## Security & Secrets

* **cert-manager** → otomatisasi sertifikat TLS (misalnya dengan Let’s Encrypt).
* **SealedSecrets** atau **ExternalSecrets** → manajemen secret yang aman dan dapat disimpan di Git.
* **OPA/Gatekeeper** → enforcement kebijakan (misalnya membatasi image container yang boleh dipakai).
* **Trivy** → scanning vulnerability pada container image.

---

## Alasan Pemilihan

1. Semua tools **100% open-source** dengan komunitas aktif.
2. Terbukti handal digunakan di lingkungan produksi.
3. Integrasi mulus dengan Kubernetes dan Helm.
4. Mendukung kebutuhan utama aplikasi LinkHub:

   * **High Availability & Scalability** → Kubernetes, HPA, Postgres Operator.
   * **Security** → cert-manager, OPA, Trivy, SealedSecrets.
   * **Observability** → Prometheus, Grafana, Loki, Jaeger.
   * **Automation** → Helm, Argo CD, Tekton.

