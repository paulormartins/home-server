# 🚀 Home Server Platform

> A production-inspired self-hosted platform built on Kubernetes for media streaming, infrastructure management, monitoring and future AI workloads.

![Kubernetes](https://img.shields.io/badge/Kubernetes-k3d-blue)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420)
![Jellyfin](https://img.shields.io/badge/Jellyfin-Media_Server-00A4DC)
![License](https://img.shields.io/badge/License-MIT-green)

---

# Overview

Home Server Platform is a personal infrastructure project designed to provide a modern, production-inspired environment for self-hosted services.

The project originally started as a simple Docker Compose deployment centered around Jellyfin and gradually evolved into a Kubernetes-based platform capable of hosting media services, monitoring tools, infrastructure dashboards and future AI workloads.

Beyond its practical use as a home server, this repository also serves as a hands-on laboratory for learning:

- Kubernetes
- Linux Administration
- Platform Engineering
- Infrastructure as Code
- Networking
- Storage Management
- Self-hosted Services

The long-term goal is to create a modular platform that can be expanded with AI services, monitoring, GitOps and automation while following industry best practices.

---

# Goals

The platform was designed with the following objectives:

- Build a production-inspired Kubernetes environment.
- Learn cloud-native infrastructure concepts.
- Centralize self-hosted services.
- Replace Docker Compose with Kubernetes workloads.
- Maintain persistent application data.
- Implement scalable networking using Traefik.
- Prepare the platform for monitoring and AI integration.

---

# Architecture

```
                          Home Network
                                │
                                │
                        Router / Local DNS
                                │
                                ▼
                        Traefik Ingress
                                │
       ┌────────────────────────┼─────────────────────────┐
       │                        │                         │
       ▼                        ▼                         ▼
   Homepage                Headlamp                  Jellyfin
                                                        │
                       ┌────────────────────────────────┼────────────────────────────┐
                       ▼                                ▼                            ▼
                    Sonarr                         Radarr                       Bazarr
                                                        │
                                                        ▼
                                                 Shared Media Storage
                                                        │
                                                        ▼
                                                      Samba
```

---

# Technology Stack

## Operating System

- Ubuntu Server/Desktop

## Container Platform

- Kubernetes (k3d)

## Networking

- Traefik Ingress Controller

## Media

- Jellyfin
- Sonarr
- Radarr
- Bazarr

## Infrastructure

- Homepage
- Headlamp

## Monitoring

- Uptime Kuma

## Storage

- Persistent Volumes
- Persistent Volume Claims

---

# Kubernetes Namespaces

The cluster is organized into dedicated namespaces.

```
homelab
│
├── Homepage

media
│
├── Jellyfin
├── Sonarr
├── Radarr
└── Bazarr

platform
│
├── Headlamp
└── Traefik

monitoring
│
└── Uptime Kuma

ai
│
└── Future AI workloads
```

Separating workloads by namespace improves organization and simplifies maintenance.

---

# Services

## Homepage

Acts as the main dashboard of the platform.

Features:

- Centralized access
- Service grouping
- Custom dashboard
- Kubernetes deployment

---

## Headlamp

Kubernetes-native dashboard replacing Portainer.

Features:

- Namespace management
- Pod inspection
- Deployment management
- Log viewer
- Events
- Persistent Volume visualization

---

## Jellyfin

Media server responsible for streaming movies and TV shows.

Features:

- Hardware transcoding
- Intel VAAPI acceleration
- SSD transcoding cache
- Persistent configuration
- Kubernetes Deployment

---

## Sonarr

TV Series automation.

Responsibilities:

- Library organization
- Metadata
- Automatic imports

---

## Radarr

Movie automation.

Responsibilities:

- Movie management
- Library organization
- Metadata

---

## Bazarr

Subtitle management.

Responsibilities:

- Subtitle download
- Automatic synchronization
- Multi-language support

---

## Uptime Kuma

Infrastructure monitoring.

Current usage:

- Service availability
- Status dashboard

Future:

- Notifications
- Alerting

---

## Samba

Network file sharing.

Current shares:

- Media Library
- Shared Documents
- Home Server Workspace

---

# Storage Layout

```
Storage

Media
│
├── Movies
├── TV Shows
├── Downloads

AppData
│
├── Jellyfin
├── Sonarr
├── Radarr
├── Bazarr
├── Homepage
└── Uptime Kuma
```

Application configuration and media libraries are intentionally separated to simplify upgrades and backups.

---

# Hardware Acceleration

Jellyfin uses Intel VAAPI for hardware transcoding.

Current implementation includes:

- Intel Iris Xe Graphics
- VAAPI
- HEVC Encoding
- H.264 Encoding
- Hardware Decoding
- SSD-based Transcoding Directory

---

# Migration History

The project evolved through several stages.

```
Docker Compose

↓

Persistent Storage

↓

Reverse Proxy

↓

Traefik

↓

Kubernetes

↓

Media Stack

↓

Infrastructure Dashboard

↓

Monitoring

↓

AI Platform
```

---

# Current Status

| Service | Kubernetes |
|----------|------------|
| Homepage | ✅ |
| Headlamp | ✅ |
| Jellyfin | ✅ |
| Sonarr | ✅ |
| Radarr | ✅ |
| Bazarr | ✅ |
| Uptime Kuma | ✅ |

---

# Repository Structure

```
home-server

docs/
infra/
scripts/

infra/
└── kubernetes/
    ├── homepage/
    ├── jellyfin/
    ├── sonarr/
    ├── radarr/
    ├── bazarr/
    ├── headlamp/
    ├── monitoring/
    └── ai/
```

---

# Design Decisions

## Why Kubernetes?

Instead of maintaining a growing Docker Compose file, Kubernetes provides:

- Better scalability
- Resource management
- Standardized deployments
- Easier automation
- Future GitOps adoption

---

## Why Traefik?

Chosen because it offers:

- Native Kubernetes integration
- Automatic Ingress discovery
- Lightweight architecture
- Future HTTPS support

---

Headlamp was selected instead of Portainer because it is Kubernetes-native and provides a better operational experience for cluster management.

---

Homepage provides a lightweight centralized dashboard for all self-hosted services.

---

# Performance Optimizations

Current optimizations include:

- Hardware video transcoding
- SSD application cache
- SSD transcoding directory
- Persistent storage
- Resource limits
- Namespace separation

---

# Roadmap

## Monitoring

- [ ] Prometheus
- [ ] Grafana
- [ ] Node Exporter
- [ ] kube-state-metrics

---

## AI

- [ ] Ollama
- [ ] Open WebUI
- [ ] OpenClaw
- [ ] Local Knowledge Base

---

## Media

- [ ] Komga
- [ ] Live TV
- [ ] Threadfin
- [ ] IPTV Integration

---

## Platform

- [ ] GitOps
- [ ] Argo CD
- [ ] Kustomize
- [ ] Automated Backups

---

