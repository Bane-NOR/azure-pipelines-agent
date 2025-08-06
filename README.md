# Azure DevOps Build Agent with Docker, Node.js, Playwright & Azure CLI

This image is based on **Ubuntu 24.04** and is designed for use in **build and release pipelines**, especially in Azure DevOps or CI/CD environments that require:
- Docker CLI & Buildx
- Node.js (v22) & npm
- Playwright testing
- Azure CLI (with AKS CLI)
- Python 3 with Kubernetes client
- Common developer & debugging tools

---

## Features

- **Base OS:** Ubuntu 24.04 (minimal, non-interactive apt configuration)
- **Docker tools:** `docker-ce`, `docker-ce-cli`, `containerd.io`, `docker-buildx-plugin`
- **Node.js v22** (via NodeSource) with npm included
- **Azure CLI** + AKS CLI
- **Python 3 full install** + `python3-kubernetes` + `pip`
- **Playwright** (installed with all dependencies)
- **Common CLI tools:** `curl`, `jq`, `git`, `zip`, `unzip`, `net-tools`, `iputils-ping`
- **Bruno CLI**, `dotenv-cli`, TypeScript, and Node.js type definitions

---

## Installed Versions

- **Ubuntu:** 24.04
- **Node.js:** 22.x
- **npm:** Bundled with Node.js
- **Docker CLI:** Latest stable from Docker’s official repo
- **Azure CLI:** Latest stable
- **Playwright:** Latest (installed via `npx playwright install --with-deps`)

---

