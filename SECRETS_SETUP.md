# Secrets Configuration Guide

This repository contains modular secret configurations organized by component for improved maintainability and deployment flexibility.

## Overview

Secrets are organized into three categories:
- **Infrastructure secrets**: Core platform access and configuration
- **Application variables**: Environment-specific settings and metadata
- **Component secrets**: Service-specific credentials and configuration

## Component Documentation

### Infrastructure & Common
- **[Infrastructure Secrets](./secrets/secrets-infrastructure.md)** - Core infrastructure access and common variables

### Infrastructure Services
- **[Redis Secrets](./secrets/secrets-redis.md)** - Redis caching and session storage
- **[MongoDB Secrets](./secrets/secrets-mongodb.md)** - MongoDB database administration
- **[RabbitMQ Secrets](./secrets/secrets-rabbitmq.md)** - RabbitMQ message queuing

### Observability Stack
- **[OpenObserve Secrets](./secrets/secrets-openobserve.md)** - Log aggregation and analytics platform
- **[Grafana Secrets](./secrets/secrets-grafana.md)** - Dashboard and visualization platform
- **[Tempo Secrets](./secrets/secrets-tempo.md)** - Distributed tracing backend
- **[OTEL Collector Secrets](./secrets/secrets-otel-collector.md)** - Telemetry collection and processing
- **[Vector Secrets](./secrets/secrets-vector.md)** - High-performance log shipping

## GitHub Repository Configuration

### Repository Secrets
Configure these as GitHub repository secrets:

- `ANSIBLE_HOSTS` - K3s server connection details
- `SSH_PRIVATE_KEY` - SSH access to servers
- `KUBECONFIG` - Kubernetes cluster configuration
- `ANSIBLE_EXTRA_SECRETS_JSON` - Application-specific secrets (JSON format)

### Repository Variables
Configure these as GitHub repository variables:

- `ANSIBLE_EXTRA_ENV_JSON` - Common environment variables (JSON format)
- `AUTO_DEPLOY` - Enable/disable automatic deployments

## Component-Specific Details

Refer to individual component documentation in the `secrets/` directory for detailed secret requirements and configuration examples.
