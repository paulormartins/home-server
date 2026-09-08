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

## Phase 11 - Kubernetes Migration & Distributed Transcoding (k3d + rffmpeg)

Migration of core homelab media workloads to Kubernetes (k3d) and distributed real-time transcoding offload.

Activities:

* k3d lightweight Kubernetes cluster deployed on Ubuntu host.
* Jellyfin, Radarr, Sonarr, Transmission deployed as containerized pods.
* Remote hardware-accelerated transcoding engine (`rffmpeg`) offloading live playback to a remote Windows 11 / WSL2 worker equipped with an NVIDIA GeForce RTX 5070.
* Automated fallback wrapper (`ffmpeg-fallback-wrapper`) providing graceful degradation to local CPU/VAAPI when the GPU worker is offline.

Benefits:

* Near-instant live stream startup without loading the central server CPU.
* True declarative infrastructure with Kubernetes manifests.

---

## Phase 12 - Distributed Batch Transcoding (Media-Farm Map-Reduce)

Implementation of high-performance distributed batch media processing via Map-Reduce Parallel Media Chunking.

Architecture:

* **Brain**: Central Ubuntu server (`192.168.x.xx:xxxx`) managing SQLite job queues, hierarchical job schemas, and reduce operations.
* **Split Engine (`chunker.py`)**: Instant packet-level inspection (`ffprobe -show_packets`) determining keyframe-aligned, non-overlapping cuts without video decoding.
* **GPU Worker Daemon (`jobd.py`)**: Multi-threaded worker pool on WSL2 executing up to 2 simultaneous NVENC sessions in pure CUDA hardware acceleration (`hevc_nvenc`).
* **Reduce Engine (`reducer.py`)**: Lossless FFmpeg concatenation (`-c copy`) and master audio/subtitle remux preserving Dolby Atmos, TrueHD, DTS-HD MA, PGS, and chapters with duration integrity verification.

Benefits:

* Accelerates 4K media encoding linearly across GPU engines.
* Reduces multi-hour encodes to minutes with 100% audio and metadata parity.

---

## Phase 13 - Automated 4K Media Ingestion via Arr Webhooks

Fully automated, hands-off background optimization pipeline triggered by media acquisition.

Features:

* **Webhook Endpoints (`api.py`)**: `POST /hooks/radarr`, `POST /hooks/sonarr`, and unified `POST /hooks/arr`.
* **Asynchronous Immediate Response (`202 Accepted`)**: Prevents webhook timeouts in Radarr/Sonarr by dispatching tasks to FastAPI background runners.
* **Intelligent 4K Filtering**: Automatically detects 2160p resolution from download/upgrade event payloads or ffprobe container inspection, skipping 1080p/720p content with zero GPU overhead.
* **Concurrency Locking & Duplicate Guard**: File-level locks prevent race conditions; existing healthy `[web].mkv` companion files are skipped automatically.
* **Jellyfin Library Auto-Refresh**: Calls `POST /Library/Refresh` immediately upon successful Reduce completion, indexing the optimized companion media without waiting for periodic scheduled scans.

Benefits:

* Zero manual intervention required from download to optimized playback.
* Preserves original pristine UHD remux files while providing an instant, lightweight companion file for direct play on web, mobile, and remote clients.

---

## Current State

Infrastructure currently provides:

* Media streaming with distributed real-time NVENC transcoding (Jellyfin + rffmpeg + RTX 5070)
* Autonomous 4K batch Map-Reduce media optimization pipeline (`media-farm`)
* Automated webhook-driven media ingestion from Radarr and Sonarr
* Instant Jellyfin library indexing on completion
* Declarative Kubernetes cluster workloads (k3d)
* Shared network storage across Windows, macOS, and Linux (Samba / CIFS)
* Container and stack management (Portainer)
* Service availability monitoring (Uptime Kuma)
* Reverse proxy with internal domains (Traefik & Nginx Proxy Manager)
* Single-pane homelab dashboard (Homepage)
* Automated backup routines

---

## Future Roadmap

* Multi-worker GPU clustering (dynamically aggregating additional compute nodes)
* AV1 NVENC dual-profile generation for supported modern web clients
* Real-time web dashboard for media-farm job queue & GPU telemetry
* Automated HDR10+ / Dolby Vision metadata tonemapping presets
* Immich deployment for centralized photo/video management
* Centralized Prometheus & Grafana homelab metrics

