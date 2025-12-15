# 🛡️ Secure & Monitored Homelab Infrastructure

Ce projet documente la mise en place d'une infrastructure de homelab auto-hébergée, robuste et sécurisée. L'objectif était de déployer des services conteneurisés tout en garantissant une haute sécurité (IPS/IDS) et une observabilité complète (Monitoring/Alerting).

![Architecture Diagram](./infra_homelab.png)
*(Voir le schéma d'architecture ci-dessus)*

## 🔒 Stack Technique

* **Infrastructure :** Freebox Ultra (VM ARM64 / Debian)
* **Conteneurisation :** Docker & Docker Compose
* **Orchestration :** Portainer
* **Reverse Proxy & SSL :** Nginx Proxy Manager (Let's Encrypt auto-renewal)
* **Sécurité (IPS/IDS) :** CrowdSec (avec bouncer pare-feu)
* **Monitoring :** Prometheus, Grafana, cAdvisor, Node Exporter
* **Disponibilité :** Uptime Kuma
* **Alerting :** Notifications Discord en temps réel

## 📊 Focus Sécurité

La sécurité est le cœur de cette infrastructure.
* **CrowdSec** analyse les logs de Nginx Proxy Manager en temps réel.
* Détection des comportements malveillants (Scans, Brute-force, User-Agents suspects).
* **Remédiation automatique :** Bannissement IP via le pare-feu (ipset/nftables) au niveau du noyau Linux.
* Gestion des "IPs de confiance" pour l'administration locale.

## 🛠️ Observabilité

Une stack complète de monitoring a été déployée pour surveiller la santé du système :
* **Prometheus** collecte les métriques système (CPU, RAM, Disque) et Docker.
* **Grafana** visualise les données via des dashboards personnalisés (y compris les métriques d'attaques CrowdSec).
* **Uptime Kuma** surveille la disponibilité des services HTTP/TCP et alerte via Discord en cas de downtime.

## 🧾 Installation

Ce projet utilise `docker-compose` pour un déploiement unifié.

1. Cloner le dépôt :
   ```bash

   git clone https://github.com/xDaJager/securehomelab.git

