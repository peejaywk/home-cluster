## Overview
This repository contains the complete setup for my homelab Kubernetes cluster. The entire cluster is managed declaratively using GitOps principles, with FluxCD continuously reconciling the desired state defined in this repository. Renovate automatically monitors dependencies and creates pull requests to keep applications up to date.

The cluster runs on [K3s](https://k3s.io/), a lightweight Kubernetes distribution that is ideal for homelab environments.

## Purpose
- **Learning:** Hands-on experience with Kuberenetes and cloud native technologies
- **DevOps Skills:** Practical application of GitOps, CI/CD and infrastructure automation
- **Experimentation:** Safe environment for testing new tools and learning

## Architecture
### Staging Cluster
- Hardware: HP EliteDesk 800 G2
- OS: Ubuntu Server
- CPU: Intel i5-6500T
- Memory: 16GB RAM
- Storage: 120GB SSD

### Core Technologies
- Kubernetes: Container orchestration platform
- FluxCD: GitOps operator for continuous delivery
- Renovate: Automated dependency updates
- Prometheus: Metrics collection and monitoring
- Grafana: Visualisation and dashboards
- SOPS: Encrypted secrets management using age engryption

## Features
- **GitOps-driven:** All changes are applied through Git commits
- **Automated updates:** Renovate bot keeps applications current
- **Declarative configurations:** Everything defined as code
- **Secure Secrets**: Encrypted secret management with SOPS and age

## Automated Updates
Renovate bot is configured to
- Scan for outdated dependencies
- Create pull requests with updates
- Keep applications and infrastructure components up to date
The pull requests must be manually reviews and accepted before any updates are applied to the cluster.

## Applications
The cluster currently hosts the following applications:
- [Linkding](https://linkding.link/): Self-hosted bookmark manager for organising and archiving web bookmarks
- [Audiobookshelf](https://www.audiobookshelf.org/): Self-hosted audiobook and podcast server.
## Monitoring
The cluster includes a full monitoring stack configured in the `monitoring/` directory
- **Prometheus:** Collects and stores metrics from the cluster and applications
- **Grafana:** Provides dashboards for visualising metrics and monitoring cluster health
The monitoring dashboards are only accessible on the local network through the configured ingress endpoints.

## Development Environment
This repository includes a dev container configuration for a consistent development environment. The packages installed inside the container and environment variables are managed using [Mise](https://mise.jdx.dev/).

## TODO
- **Production Cluster:** Add a second production cluster to enable proper stage -> production deployment pipeline
	- Setup hardware for production environment
	- Configure FluxCD for multi-cluster management
	- Implement promotion strategies between staging and production
- **TrueNAS Integration:** Store databases on local TrueNAS server
	- Configure NFS/iSCSI storage provisioning
	- Setup persistent volume claims for database workloads
	- Implement different storage classes for different performance tiers (staging / production)
- **Cloud Backup:** Backup databases to the cloud
	- Configurate automated backup schedules
	- Test restore procedure
	- Test cluster re-build prosedure

---
Note: This is a homelab environment for learning purposes. Configurations may not follow best practices in all cases as experimentation is part of the learning process
