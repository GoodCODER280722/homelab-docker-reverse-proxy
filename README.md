# homelab-docker-reverse-proxy
Self-hosted homelab infrastructure built on a repurposed HP Pavillion laptop running **Linux Mint**, managed remotely via **SSH** and orchestrated using Docker, Portainer, and Nginx Proxy Manager (NPM) to manage and route multiple internal services behind clean, human-readable LAN hostnames.
This project demonstrates container orchestration, reverse proxy configuration, service monitoring, and operational troubleshooting in a LAN-based environment.

---

## Overview

Internal services are exposed via custom local hostnames using the format:

## Naming Convention

Internal services are exposed via custom local hostnames using the format:

<service>.home

Examples:
- npm.home
- portainer.home
- webtest.home

Name resolution is handled via Windows hosts file entries pointing to the server IP address.

## Architecture

### Windows Client
  ↓ (hosts file entries)
  npm.home / portainer.home / webtest.home
  ↓
Nginx Proxy Manager (reverse proxy)
  ↓ (Docker proxy network)
-------------------------------------
|           Docker Network          |
|  - NPM container                  |
|  - Portainer container            |
|  - WebTest container              |
-------------------------------------

### Internal Services
- NPM Container
- Portainer Container
- Webtest Container
- Uptime Kuma Container

   ---
  
## Monitoring

Uptime Kuma deployed as internal monitoring dashboard

Accessible at:
-http://status.home

Configured Monitors:
-npm.home
-portainer.home
-webtest.home
-status.home
---

## Technologies Used
- Linux Mint (Server OS)
- SSH remote administration
- Docker
- Docker Compose
- Nginx Proxy Manager
- Portainer CE
- Uptime Kuma
- Windows hosts-based DNS override
- SSH-based remote administration

---

## Skills Demonstrated

- Containerized service deployment
- Reverse Proxy routing configuration
- Internal hostname mapping (LAN-based DNS strategy)
- Health monitoring and validation
- Debugging proxy/network issues (502 errors, port mismatching, container networking)
- Structured infrastructure organization via Docker Compose
- Remote server management via SSH

---

## Scope

This setup is LAN-only and not exposed publicly

If exposing externally:
- Implement real DNS
- Enable TLS
- Harden admin points
- Restrict firewall or VPN

---

## Future Improvements

- Replace hosts-file naming with centralized LAN DNS (Pi-Hole, router DNS)
- Add scripted deployment workflows
- Add automated backups for volumes
- Add additional services (AI microservices, logging, etc.)
