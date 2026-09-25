# DevOps Engineer — Linux / Docker / CI/CD / Observability
[ФИО] | [Город, готов к гибриду, офису, командировкам, дежурствам] | TG: [@izislesar] | Email: [a1212gleb@gmail.com] | GitHub: [github.com/izislesar] | Телефон: [+79851185668]

## SUMMARY — афиша для хакатона и хантера
DevOps с ядром Linux-администрирования. Поднимаю инфру с нуля за часы: сервер → Docker → CI/CD → мониторинг → стрессы → дашборды. На хакатонах закрываю весь контур один: деплой, метрики Prometheus, Grafana, логи, бекапы. Подаюсь на Junior+, по факту закрываю требования Middle: продовые стенды, k6-нагрузки, burn-rate алерты, Helm/K8s.
Ищу: product DevOps/SRE, платформенную команду. Формат: фуллтайм, дежурства ок.

## SKILLS — ATS-ядро дословно под hh.ru
Languages: Go, Python, SQL, Bash
Linux: systemd, users/sudoers/SSH hardening, LVM, cron, logrotate, ufw/nftables, apt/dnf, troubleshooting: ss, ps, journalctl, dmesg, strace, tcpdump
Networks: TCP/IP, DNS, HTTP/HTTPS, TLS, Nginx reverse-proxy, upstream, proxy_pass, Certbot
Containers: Docker, Dockerfile multi-stage, Docker Compose, registry, volumes/networks, healthcheck
Orchestration: Kubernetes (k3s, minikube, managed), kubectl, Pod, Deployment, StatefulSet, Service, Ingress, ConfigMap, Secret, probes, resources, RBAC, Helm, Kustomize
CI/CD: GitLab CI, GitHub Actions, Jenkins, runners, artifacts/cache, deploy strategies, rollback by SHA
IaC: Terraform, OpenTofu, Terragrunt base, Ansible (playbook, role, vault, inventory)
Observability: Prometheus, PromQL, Alertmanager, Grafana, Loki, Promtail, LogQL, node_exporter, cAdvisor, blackbox_exporter, OpenTelemetry base, Jaeger/Tempo base
Databases: PostgreSQL (psql, pg_dump/pg_restore, PITR base, PgBouncer base), MySQL, Redis, S3-совместимое хранилище (MinIO/Yandex Object Storage)
Load Testing: k6, Locust, wrk — RPS/latency p95/p99, узкие места app/DB
Cloud: Yandex Cloud, Selectel (VM, VPC, Security Groups, IAM, Object Storage), Proxmox base, bare-metal
Git: git, rebase/merge, cherry-pick, GitFlow/trunk-based, MR review
Security base: Vault/SOPS/Sealed Secrets, Trivy, NetworkPolicy

## EXPERIENCE
### DevOps Engineer (homelab + commercial + hackathons) — 2023 — н.в.
Homelab: 3x VPS + домашний сервер (Arch/Debian/Ubuntu) — держу постоянно, все pet-проекты там.
- Администрирование: systemd-юниты, SSH-only, ufw whitelist, LVM, автообновления без даунтайма
- CI/CD с нуля: GitLab CI build/test/push/deploy, теги по SHA, откат одной командой
- Docker-конвейер: все сервисы в Compose, multi-stage образы <150MB, .dockerignore, non-root USER
- Monitoring: Prometheus + Grafana + Alertmanager в TG (down, disk>80%, 5xx-rate), Loki для логов, дашборды CPU/RAM/Disk/RPS/p95
- Load tests: k6/Locust на каждый стенд до 200 RPS, нахожу бутылку (DB pool / upstream timeout) до прода
- Backup/Restore: pg_dump в cron + S3, восстановление проверено удалением volume

### Хакатоны — DevOps/инфра [указать 2-3 названия, год, место]
- [Хакатон 1 — роль DevOps, топ-N]: поднял инфу команды за 2 часа (VM + Docker + CI + домен + TLS), команда пилила фичи а не чинила деплой
- [Хакатон 2]: Grafana-дашборд + k6-стресс + алерты, нашли просадку p99 до демо, пофиксили pool Postgres
- Ссылки: [GitHub org хакатона / демо-видео]

### [Коммерческий опыт / фриланс — Компания, 20XX-20XX] — заполнить 2 строки
- [Что держал: N серверов, что катал, какой uptime/MTTR]
- [Что автоматизировал: Ansible/Terraform, сколько часов toil срезал]

## PROJECTS — пруфы кодом
**infra-realworld — полный DevOps-цикл вокруг чужого бэка (Django/FastAPI) [github link]**
Terraform (VM+SG+S3) / Ansible (base/docker/monitoring) / Docker Compose (app+postgres+nginx+promtail) / GitLab CI / Prometheus+Grafana+Loki
- HTTPS Nginx+Certbot, миграции отдельным job, rollback по SHA
- k6: 150 RPS, p95 <400ms, отчет в репо

**infra-kuma-k8s — K8s-стенд [github link]**
k3s via Ansible / свой Helm-chart (Deployment+PVC+Ingress+probes) / kube-prometheus-stack
- Kill-pod → self-healing 30-40s, PVC выживает, MTTR замерен
- Chaos: kill node, disk pressure via fallocate, дока в README

**go-pg-exporter / py-backup-tool [github link]**
Go: мини-exporter (http + prometheus-client, горутины). Python: бекап-тул (boto3 + argparse + cron) — pg_dump → S3 → TG-уведомление.

## ATS-ХВОСТ — ключевики строкой для парсера
DevOps, SRE, Linux, Docker, Kubernetes, k3s, Helm, GitLab CI, GitHub Actions, Jenkins, Ansible, Terraform, OpenTofu, Prometheus, Grafana, Loki, PostgreSQL, Redis, Nginx, Bash, Python, Go, SQL, k6, Yandex Cloud, Selectel, CI/CD, monitoring, logging

## ABOUT
Английский: чтение доков свободно, разговорный базовый. Быстро вникаю в чужой код (Go/Python), не боюсь прод-дежурств, пишу runbook чтобы ночью не будили дважды по одному поводу.

