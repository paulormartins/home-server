# Project History

## Phase 1 - Base System

The project started with the installation and configuration of an Ubuntu host intended to serve as a centralized home server.

Objectives:

* Centralize services
* Provide network storage
* Create a media platform
* Learn infrastructure administration

---

## Phase 2 - Docker Environment

Docker and Docker Compose were installed to simplify application deployment and maintenance.

Benefits:

* Isolated environments
* Easy service management
* Simplified updates
* Reproducible deployments

---

## Phase 3 - Media Server

Jellyfin was deployed as the primary media platform.

Activities:

* Container deployment
* Media library configuration
* Remote access testing
* Smart TV integration

Lessons learned:

* Volume management
* Container persistence
* Media organization

---

## Phase 4 - File Sharing

Samba was implemented to provide file sharing across multiple operating systems.

Activities:

* Shared folder creation
* Permission management
* Windows integration
* macOS integration

Lessons learned:

* Network file sharing
* Linux permissions
* SMB configuration

---

## Phase 5 - Reverse Proxy

Nginx Proxy Manager was deployed to simplify access to services.

Before:

```text
Service:Port
```

After:

```text
service.home
```

Benefits:

* Cleaner URLs
* Centralized routing
* Easier service discovery

---

## Phase 6 - Infrastructure Management

Portainer was added to simplify Docker administration.

Activities:

* Container management
* Stack administration
* Environment monitoring

Benefits:

* Reduced operational complexity
* Centralized management

---

## Phase 7 - Monitoring

Uptime Kuma was deployed to monitor service availability.

Monitored services:

* Jellyfin
* Portainer
* Reverse Proxy
* Internal services

Benefits:

* Service visibility
* Availability monitoring
* Faster troubleshooting

---

## Phase 8 - Dashboard

Homepage was implemented as the primary entry point for the homelab.

Features:

* Service catalog
* Resource monitoring
* Infrastructure overview

Benefits:

* Single-pane management
* Improved usability

---

## Phase 9 - Backup Strategy

A backup process was implemented to protect critical configuration data.

Protected components:

* Docker stacks
* Proxy configuration
* Samba configuration
* System settings
* Portainer data

Benefits:

* Faster recovery
* Reduced operational risk

---

## Phase 10 - DNS Evaluation

AdGuard Home was deployed for testing and future DNS management.

Current status:

* Evaluation environment
* Not yet acting as primary DNS

Potential future use:

* DNS management
* Ad blocking
* Local service discovery

---

## Current State

Infrastructure currently provides:

* Media streaming
* File sharing
* Container management
* Service monitoring
* Reverse proxy management
* Dashboard access
* Backup automation

---

## Future Roadmap

* Storage optimization
* Immich deployment
* Infrastructure as Code
* Monitoring enhancements
* Kubernetes laboratory
* Centralized logging
* Disaster recovery testing

```
```
