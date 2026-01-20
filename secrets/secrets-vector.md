# Vector Secrets Setup

This file contains secrets required for Vector deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## Required Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Vector requires OpenObserve credentials for log export. Make sure you have configured [OpenObserve secrets](./secrets-openobserve.md):

```json
{
  "ZO_ROOT_USER_EMAIL": "admin@yourdomain.com",
  "ZO_ROOT_USER_PASSWORD": "your-secure-password"
}
```

## Component Overview

Vector is a high-performance log shipper that collects, transforms, and routes logs.

**Data Flow:**
- Collects logs from various sources (files, systemd, kubernetes, etc.)
- Transforms and enriches log data
- Ships logs to OpenObserve for storage and analysis

## Configuration

Vector is configured to:
- Collect logs from Kubernetes pods and nodes
- Parse and structure log data
- Export logs to OpenObserve with proper authentication
- Handle log rotation and buffering

## Security Notes

- Uses OpenObserve credentials for authentication to the log destination
- Ensure OpenObserve is deployed before Vector
- Credentials are stored in Kubernetes secrets and used for API authentication
- Monitor authentication failures and credential rotation

## Deployment Order

1. [OpenObserve](./secrets-openobserve.md) (provides the log destination)
2. Vector (ships logs to OpenObserve)
3. [Grafana](./secrets-grafana.md) (visualizes the collected logs)

## Troubleshooting

- Check OpenObserve connectivity and authentication
- Verify log collection sources are properly configured
- Review Vector logs for parsing or export errors
- Ensure network policies allow communication to OpenObserve

## Related Documentation

- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements
- [OpenObserve Secrets](./secrets-openobserve.md) - Required log destination