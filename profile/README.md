<div align="center">

# Audaks Cloud System

**Private OpenStack cloud infrastructure, built and run as code.**

![OpenStack](https://img.shields.io/badge/OpenStack-2025.2-ED1944?logo=openstack&logoColor=white)
![Kolla-Ansible](https://img.shields.io/badge/deployed%20with-Kolla--Ansible-1A1918?logo=ansible&logoColor=white)
![Ubuntu](https://img.shields.io/badge/base-Ubuntu-E95420?logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/runtime-Docker-2496ED?logo=docker&logoColor=white)

</div>

---

## About

Audaks Cloud System designs, deploys and operates a production OpenStack cloud.
Every part of the platform, from container images to service configuration, lives in
version-controlled code and is rolled out with Kolla and Kolla-Ansible.

## Platform

| Layer | What we run |
| --- | --- |
| **Compute** | Nova on KVM, with SSH-based live migration |
| **Networking** | Neutron with Open vSwitch, provider networks, segments, QoS, VPNaaS, metering, HA agents |
| **Storage** | Ceph for images and volumes, Cinder (iSCSI backends) with volume backup |
| **Images** | Glance with image cache |
| **Load balancing** | Octavia (LBaaS), HAProxy + Keepalived for API high availability |
| **Containers** | Magnum for Kubernetes clusters |
| **Orchestration** | Heat, Mistral |
| **Identity & secrets** | Keystone, Barbican |
| **Telemetry** | Ceilometer, Gnocchi, Aodh |
| **Dashboard** | Horizon |

### Operations

- **High availability**: 3-node control plane, redundant network nodes, MariaDB with ProxySQL, RabbitMQ, Valkey
- **Security**: TLS on internal and external API endpoints
- **Monitoring**: Prometheus, Alertmanager and Grafana with exporters for every layer
- **Logging**: central logging with Fluentd and OpenSearch
- **Backups**: scheduled database backups with Mariabackup
- **Multi-region**: designed to grow across multiple regions

## How we work

```text
kolla          →  build custom container images
kolla-ansible  →  deploy and upgrade services across all nodes
inventory      →  one source of truth for node roles
globals.yml    →  one source of truth for enabled services
```

Changes go through pull requests and are reviewed before they reach production.

## Repositories

| Repository | Description |
| --- | --- |
| `audaks-core` | Core OpenStack deployment: inventory, Kolla configuration and custom images |

---

<div align="center">
<sub>Audaks Cloud System · Infrastructure as Code</sub>
</div>
