# homelab-docker-reverse-proxy
Self-hosted homelab using Docker, Portainer, and Nginx Proxy Manager with reverse proxy routing.

## Naming Convention

Internal services are exposed via custom local hostnames using the format:

<service>.home

Examples:
- npm.home
- portainer.home
- webtest.home

Name resolution is handled via Windows hosts file entries pointing to the server IP address.

## Architecture

Windows Client
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
