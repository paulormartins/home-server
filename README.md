# Home Server

A personal self-hosted homelab environment built on Ubuntu and Docker.

The objective of this project is to provide media streaming, file sharing, service monitoring, reverse proxy management, and infrastructure administration while serving as a practical learning platform for Linux, networking, Docker, and DevOps concepts.

---

# Architecture

```text
Client Devices
├── Windows
├── macOS
├── Smart TV
└── Mobile Devices

        │

        ▼

Nginx Proxy Manager
        │

        ▼

Docker Host (Ubuntu)
├── Jellyfin
├── Samba
├── Homepage
├── Uptime Kuma
├── Portainer
└── AdGuard Home

        │

        ▼

External Storage
```

---

# Services

## Jellyfin

Self-hosted media server used for:

* Movie streaming
* TV show streaming
* Media library management
* Multi-device access

---

## Samba

Network file sharing service.

Features:

* Windows support
* macOS support
* Centralized file repository
* Shared media storage

---

## Portainer

Container management platform.

Features:

* Docker administration
* Container management
* Volume management
* Stack deployment

---

## Nginx Proxy Manager

Reverse proxy solution used to simplify service access.

Examples:

* jellyfin.home
* portainer.home
* uptime.home
* homepage.home

Benefits:

* Friendly URLs
* Centralized access
* Easier service discovery

---

## Homepage

Centralized dashboard for infrastructure access.

Features:

* Service catalog
* Resource monitoring
* Infrastructure overview

---

## Uptime Kuma

Monitoring platform used to track service availability.

Monitored services:

* Jellyfin
* Portainer
* Nginx Proxy Manager
* Internal infrastructure services

Features:

* Availability monitoring
* Response time tracking
* Status dashboard

---

## AdGuard Home

DNS and network management platform.

Current status:

* Installed for evaluation
* Not yet acting as primary network DNS

Potential future use:

* DNS management
* Ad blocking
* Local service discovery

---

# Monitoring

The environment includes monitoring for:

* CPU utilization
* Memory utilization
* Storage utilization
* Service availability

Monitoring is available through Homepage and Uptime Kuma.

---

# Backup Strategy

The environment includes automated backup procedures for:

* Docker Compose stacks
* Samba configuration
* System configuration files
* Portainer data
* Infrastructure configuration

Backups are stored in dedicated locations and can be used to rebuild the environment.

---

# Technologies

* Ubuntu Linux
* Docker
* Docker Compose
* Jellyfin
* Samba
* Portainer
* Nginx Proxy Manager
* Homepage
* Uptime Kuma
* AdGuard Home

---

# Learning Objectives

This homelab serves as a practical learning environment for:

* Linux Administration
* Networking
* Docker
* Infrastructure Monitoring
* Reverse Proxy Management
* Backup and Recovery
* Self-Hosting
* DevOps Practices

---

# Future Improvements

Planned enhancements include:

* Storage optimization
* Immich deployment
* Infrastructure as Code
* Kubernetes laboratory environment
* Advanced monitoring
* Centralized logging
* Disaster recovery testing

---

# Disclaimer

Sensitive information such as:

* Internal IP addresses
* Credentials
* Usernames
* Network topology details
* Secrets and tokens

has been intentionally omitted from this public repository.

```
```
