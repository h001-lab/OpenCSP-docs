# OpenCSP Documentation

This repository contains the technical specifications and architectural guides for OpenCSP.

## Key Features
- **Declarative Infrastructure**: Manage Proxmox resources via Terraform (OpenTofu) CRs.
- **GitOps Native**: Automated reconciliation using Flux CD and Tofu-controller.
- **Secure by Design**: Integrated IAM with ZITADEL and automated security hardening via Ansible.
- **Full Observability**: Automated OTel collector deployment for every instance.

## Tech Stack
- **Control Plane**: K3s (Lightweight Kubernetes)
- **IAM**: ZITADEL (OIDC)
- **Provisioning**: OpenTofu (via Tofu-controller)
- **Post-Config**: Ansible Semaphore
- **Frontend**: Next.js & Next-auth

## Documentation
- [System Architecture](./docs/Architectures/architectures.md)
- [Operational Flows](./docs/Flows/flows.md)
- [Getting Started](./docs/Installation/guide.md)

## License
OpenCSP follows a multi-license model to balance community growth and project protection:
- **Core Platform (Console, Ops, Docs)**: Licensed under the [GNU Affero General Public License v3 (AGPL-3.0)](./LICENSE). Unlike standard GPL, AGPL requires that the modified source code be made available to any user interacting with the software over a network.
- **Infrastructure Modules**: Licensed under the [Apache License 2.0](https://github.com/h001-lab/OpenCSP-modules?tab=Apache-2.0-1-ov-file) to encourage widespread adoption and vendor integration.