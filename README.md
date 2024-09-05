<div align="center">

  [![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.27.2-blue?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
  [![Linux](https://img.shields.io/badge/Talos-v1.4.5-blue?style=for-the-badge&logo=linux&logoColor=white)](https://kubernetes.io/)

</div>

## 📖 Table of contents

- [📖 Table of contents](#-table-of-contents)
- [📋 Requirements](#-requirements)
- [🚀 Quick Start](#-quick-start)
- [🔧 Hardware](#-hardware)
- [☁️ Cloud Services](#️-cloud-services)
- [🖥️ Technology Stack](#️-technology-stack)
- [🤝 Acknowledgments](#-acknowledgments)

## 📋 Requirements

- [Kubernetes](https://kubernetes.io/) cluster
- [Flux CLI](https://toolkit.fluxcd.io/get-started/) installed
- [Kustomize](https://kustomize.io/) installed
- [Taskfile](https://taskfile.dev/) installed

## 🚀 Quick Start
1. Provision 2 Talos nodes in to maintanence mode

2. Run taskfile to create a talos control node:

```bash
CTRL_IP=x.x.x.x
export CTRL_IP
go-task talos:control-create
go-task talos:bootstrap
```
3. Run taskfile to create a talos worker node:

```bash
WORKER_IP=x.x.x.x
export WORKER_IP
go-task talos:worker-create
```

4. Set up the necessary environment variables for flux:

```bash
export GITHUB_USER=<your-username>
export GITHUB_REPO=<your-repo>
export CLUSTER=<target-cluster>
```

5. Verify that your cluster satisfies prerequisites:

```bash
flux check --pre
```

6. Run taskfile to deploy flux:


```bash
go-task flux
```

## 🔧 Hardware

| Device                                                                                 | Description              | Quantity | CPU     | RAM      | Architecture | Operating System                      | Notes |
| -------------------------------------------------------------------------------------- | ------------------------ | -------- | ------- | -------- | ------------ | ------------------------------------- | ----- |
| Synology DS218play                                | NAS        | 1 | 04 Cores | 01GB RAM | AARCH64 | [DSM 7](https://www.synology.com/en-us/dsm) | |
| Intel NUC12WSHi3                                  | Hypervisor | 1 | 10 Cores | 32GB RAM | AMD64   | [Proxmox 8.3](https://proxmox.com/en/) | |
| Intel NUC12WSHi5 Slim                             | Hypervisor | 1 | 12 Cores | 64GB RAM | AMD64   | [Proxmox 8.3](https://proxmox.com/en/) | |
| HP EliteDesk 800 (g4)                             | Hypervisor | 1 | 06 Cores | 32GB RAM | AMD64   | [Proxmox 8.3](https://proxmox.com/en/) | |

## ☁️ Cloud Services

| Service                                   | Description                                                                                                                     | Cost (USD/GBP)     |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| [Cloudflare](https://www.cloudflare.com/) | I use Cloudflare in my home network for DNS management.                      | Free        |
| [GitHub](https://github.com/)             | I use GitHub for code management and version control, enabling seamless collaboration in addition to OAuth for authentication   | Free           |
| [Lets Encrypt](https://letsencrypt.org/)  | I use Let's Encrypt to generate certificates for secure communication within my network.                                        | Free           |
|                                           |                                                                                                                                 | Total: Free |

## 🖥️ Technology Stack

|                                                                                                                             | Name                                             | Description                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| <img width="32" src="https://www.talos.dev/images/logo.svg">                                                                | [Talos Linux](https://www.talos.dev/)            | Talos Linux is Linux designed for Kubernetes                                                                               |
| <img width="32" src="https://github.com/cncf/artwork/blob/main/projects/kubernetes/icon/color/kubernetes-icon-color.svg">       | [Kubernetes](https://kubernetes.io/)             | An open-source system for automating deployment, scaling, and management of containerized applications                     |
| <img width="32" src="https://github.com/cncf/artwork/blob/main/projects/flux/icon/color/flux-icon-color.svg">                   | [FluxCD](https://fluxcd.io/)                     | GitOps tool for deploying applications to Kubernetes                                                                       |
| <img width="32" src="https://github.com/cncf/artwork/blob/main/projects/helm/icon/color/helm-icon-color.svg">                   | [Helm](https://helm.sh)                          | The Kubernetes package manager                                                                                             |
| <img width="32" src="https://cncf-branding.netlify.app/img/projects/openebs/icon/color/openebs-icon-color.svg">             | [Mayastor](mayastor.gitbook.io/introduction/)                    | Container-attached storage CNCF subproject of OpenEBS                                                                                                 |
| <img width="32" src="https://github.com/cncf/artwork/blob/main/projects/cert-manager/icon/color/cert-manager-icon-color.svg">                                                     | [Cert Manager](https://cert-manager.io/)         | X.509 certificate management for Kubernetes                                                                                |

