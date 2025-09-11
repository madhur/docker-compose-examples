# Homelab Docker Compose Services

This repository contains Docker Compose configurations for various self-hosted services in my homelab environment. All services are configured to work together with Traefik as a reverse proxy and are accessible through custom domains with SSL certificates.

## 🏗️ Architecture Overview

- **Reverse Proxy**: Traefik with Let's Encrypt SSL certificates
- **Network**: External `proxy-network` for service communication
- **VPN**: WireGuard VPN for secure remote access
- **Monitoring**: Watchtower for automatic updates, Ntfy for notifications
- **Storage**: Various databases and persistent volumes

## 📋 Services

### Core Infrastructure
- **[Traefik](traefik/)** - Reverse proxy with automatic SSL certificates
- **[Portainer](portainer/)** - Docker container management UI
- **[Nginx Proxy Manager](nginxproxymanager/)** - Alternative reverse proxy solution
- **[Watchtower](watchtower/)** - Automatic Docker container updates
- **[WireGuard Easy](wg-easy/)** - VPN server for remote access

### Media & Content Management
- **[Immich](immich/)** - Self-hosted photo and video backup solution
- **[PhotoPrism](photoprism/)** - AI-powered photo management
- **[Paperless-ngx](paperless/)** - Document management system

### Security & Authentication
- **[Vaultwarden](vaultwarden/)** - Self-hosted Bitwarden password manager
- **[LLDAP](lldap/)** - Lightweight LDAP server

### Development & DevOps
- **[Jenkins](jenkins/)** - CI/CD automation server
- **[Nexus](nexus/)** - Artifact repository manager
- **[Portainer](portainer/)** - Container orchestration UI

### Databases & Storage
- **[MongoDB](mongodb/)** - NoSQL database
- **[Redis Cluster](redis-cluster/)** - In-memory data store cluster
- **[Redis MQ Kafka](redis-mq-kafka/)** - Message queue with Kafka
- **[DynamoDB](dynamodb/)** - NoSQL database (local instance)
- **[Scylla](scylla/)** - High-performance NoSQL database
- **[Elasticsearch](elasticsearch/)** - Search and analytics engine

### Monitoring & Analytics
- **[cAdvisor](cadvisor/)** - Container resource monitoring
- **[Graphite + StatsD + Grafana](graphite-statsd-grafana/)** - Metrics collection and visualization
- **[Change Detection](changedetection/)** - Website change monitoring

### Utilities
- **[Ntfy](ntfy/)** - Push notifications service
- **[Sterling PDF](sterlingpdf/)** - PDF processing service

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose installed
- External `proxy-network` created
- Domain names configured with DNS pointing to your server

### Setup
1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd docker
   ```

2. Create the external network:
   ```bash
   docker network create proxy-network
   ```

3. Navigate to any service directory and start it:
   ```bash
   cd traefik
   docker-compose up -d
   ```

## 🔧 Configuration

### Environment Variables
Most services use `.env` files for configuration. Key variables include:
- Domain names (e.g., `immich.desktop.madhur.co.in`)
- Database credentials
- Upload locations
- Timezone settings (`Asia/Kolkata`)

### Network Configuration
- **proxy-network**: External network for service communication
- **wg**: WireGuard VPN network (10.42.42.0/24)
- **elastic**: Elasticsearch cluster network

### Security Features
- VPN whitelist middleware for sensitive services
- SSL certificates via Let's Encrypt
- Container security options (no-new-privileges)
- Network isolation

## 📊 Monitoring

- **Watchtower**: Monitors for container updates and sends notifications via Ntfy
- **cAdvisor**: Provides container resource usage metrics
- **Grafana**: Visualizes metrics from Graphite/StatsD
- **Ntfy**: Push notifications for system events

## 🔒 Security

- All services behind Traefik reverse proxy
- SSL/TLS encryption for all web services
- VPN access required for sensitive services
- Regular automatic updates via Watchtower

## 📁 Directory Structure

```
docker/
├── traefik/                 # Reverse proxy
├── portainer/              # Container management
├── immich/                 # Photo backup
├── paperless/              # Document management
├── vaultwarden/            # Password manager
├── wg-easy/                # VPN server
├── elasticsearch/          # Search engine
├── mongodb/                # NoSQL database
├── redis-cluster/          # Redis cluster
├── jenkins/                # CI/CD
├── nexus/                  # Artifact repository
├── grafana/                # Monitoring dashboard
├── ntfy/                   # Notifications
└── ...                     # Other services
```

## 🌐 Access URLs

Services are accessible via the following domains (replace with your actual domains):
- Traefik Dashboard: `https://traefik.desktop.madhur.co.in:8081`
- Immich: `https://immich.desktop.madhur.co.in`
- Paperless: `https://paperless.desktop.madhur.co.in`
- Vaultwarden: `https://vault.madhur.co.in`
- WireGuard: `https://wg.desktop.madhur.co.in`
- Ntfy: `https://ntfy.madhur.co.in`

## 🔄 Maintenance

- **Updates**: Watchtower automatically updates containers
- **Backups**: Regular backups of persistent volumes recommended
- **Monitoring**: Check logs via Portainer or `docker logs <container-name>`
- **SSL**: Certificates automatically renewed by Traefik

## 📝 Notes

- VPN whitelist middleware applied to sensitive services
- External network `proxy-network` must be created before starting services
- Some services require additional configuration files (`.env`, etc.)

## 🤝 Contributing

This is a personal homelab setup. Feel free to use these configurations as reference for your own homelab.

## 📄 License

This repository contains Docker Compose configurations for self-hosted services. Please refer to individual service licenses for specific terms.

