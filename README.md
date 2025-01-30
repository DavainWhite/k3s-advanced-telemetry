# K3s Advanced Telemetry

[![GitHub Stars](https://img.shields.io/github/stars/DavainWhite/k3s-advanced-telemetry?style=social)](https://github.com/DavainWhite/k3s-advanced-telemetry/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/DavainWhite/k3s-advanced-telemetry?style=social)](https://github.com/DavainWhite/k3s-advanced-telemetry/network/members)
[![GitHub Issues](https://img.shields.io/github/issues/DavainWhite/k3s-advanced-telemetry)](https://github.com/DavainWhite/k3s-advanced-telemetry/issues)
[![GitHub License](https://img.shields.io/github/license/DavainWhite/k3s-advanced-telemetry)](./LICENSE)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/DavainWhite/k3s-advanced-telemetry)](https://github.com/DavainWhite/k3s-advanced-telemetry/commits/main)
[![GitHub Repo Size](https://img.shields.io/github/repo-size/DavainWhite/k3s-advanced-telemetry)](https://github.com/DavainWhite/k3s-advanced-telemetry)
[![Open Source](https://badgen.net/badge/Open%20Source/MIT/blue)](./LICENSE)

## Overview

K3s Advanced Telemetry is a fully open-source, pre-configured observability stack for lightweight Kubernetes (K3s) deployments. It provides a robust monitoring and alerting solution leveraging Prometheus, Grafana, and Alertmanager, optimized for resource-efficient telemetry collection in edge, cloud, and on-premise environments.

Designed as a plug-and-play telemetry solution, this project offers seamless deployment, pre-built dashboards, and a scalable architecture to meet both development and production observability needs.

## Features

- 🚀 **One-Command Deployment**: Deploy the entire telemetry stack effortlessly with `tilt up`.
- 📊 **Pre-configured Dashboards**: Includes Grafana dashboards for Kubernetes, Prometheus, and cloud-native applications.
- 🔔 **Integrated Alerting**: Features Alertmanager for proactive notifications and incident response.
- 🔄 **Lightweight & Efficient**: Optimized for K3s and resource-constrained environments.
- 🔧 **Production-Ready**: Adaptable for local, edge, and cloud deployments.

## Deployment

Ensure [Tilt](https://tilt.dev/) is installed, then deploy with:

```sh
tilt up
```

This will automatically provision the full telemetry stack within your Kubernetes cluster.

## Architecture

The K3s Advanced Telemetry stack consists of:
- **Grafana**: Real-time visualization of metrics with pre-configured dashboards.
- **Prometheus**: Scalable time-series data collection and monitoring.
- **Alertmanager**: Automated alerting for anomaly detection and incident management.
- **Kubernetes Manifests**: Managed with Kustomize for easy adaptation to various environments.

## License

This project is licensed under the **MIT License**, ensuring full open-source accessibility. See the [LICENSE](./LICENSE) file for more details.
