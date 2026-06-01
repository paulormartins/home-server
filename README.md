Home Server

A personal self-hosted home server built on Ubuntu and Docker, designed to provide media streaming, file sharing, monitoring, reverse proxy management, and infrastructure administration.

Overview

This project documents the implementation of a lightweight homelab environment using containerized services.

The goal is to provide a centralized platform for:

Media streaming
File sharing
Service monitoring
Container management
Reverse proxy management
Infrastructure experimentation
Architecture
Client Devices
├── Windows
├── macOS
├── Smart TV
└── Mobile Devices

        │

        ▼

Reverse Proxy
├── Nginx Proxy Manager

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

Storage
└── External Media Drive
Services
Jellyfin

Self-hosted media server used for:

Movie streaming
TV show streaming
Media library management

Features:

Multi-device access
Hardware acceleration support
Centralized media catalog
Samba

File sharing service used to provide network storage access.

Features:

Cross-platform compatibility
Windows and macOS support
Shared media repository
Portainer

Docker management interface.

Features:

Container administration
Volume management
Stack deployment
Environment monitoring
Nginx Proxy Manager

Reverse proxy solution used to simplify service access.

Features:

Friendly URLs
Proxy host management
SSL support
Centralized routing
Homepage

Centralized dashboard used as the primary entry point for all services.

Features:

Service shortcuts
Resource monitoring
Infrastructure overview
Uptime Kuma

Monitoring platform used to verify service availability.

Monitored services:

Jellyfin
Portainer
Reverse Proxy
Internal Services

Features:

Availability checks
Response time tracking
Status dashboard
AdGuard Home

DNS filtering and network management platform.

Current status:

Installed for evaluation and testing
Not yet acting as the primary network DNS

Potential future use:

DNS management
Ad blocking
Local service discovery
Backup Strategy

A custom backup script is used to preserve critical configuration files.

Protected components:

Docker Compose stacks
Reverse proxy configuration
Samba configuration
System configuration files
Portainer data

Backups are generated automatically and stored in dedicated backup locations.

Monitoring

The environment includes:

CPU monitoring
Memory monitoring
Storage monitoring
Service availability monitoring

Monitoring is exposed through Homepage and Uptime Kuma.

Future Improvements

Planned enhancements include:

Storage optimization
Container health monitoring
Automated disaster recovery procedures
Infrastructure as Code
Kubernetes migration laboratory
Photo management platform (Immich)
Centralized logging
Technologies
Ubuntu Linux
Docker
Docker Compose
Jellyfin
Samba
Portainer
Nginx Proxy Manager
Homepage
Uptime Kuma
AdGuard Home
Learning Objectives

This environment serves as a practical laboratory for:

Linux administration
Container orchestration
Self-hosting
Networking
Reverse proxy management
Infrastructure monitoring
Backup and recovery
DevOps practices
