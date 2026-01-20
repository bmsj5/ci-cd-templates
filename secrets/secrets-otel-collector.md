# OTEL Collector Secrets Setup

This file contains secrets required for OpenTelemetry Collector deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## Required Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

The OTEL Collector requires OpenObserve credentials for data export. Make sure you have configured [OpenObserve secrets](./secrets-openobserve.md):

```json
{
  "ZO_ROOT_USER_EMAIL": "admin@yourdomain.com",
  "ZO_ROOT_USER_PASSWORD": "your-secure-password"
}
```

## Component Overview

The OpenTelemetry Collector receives, processes, and exports telemetry data (traces, metrics, logs).

**Data Flow:**
- Receives telemetry from applications and infrastructure
- Processes and enriches data with environment labels
- Exports to OpenObserve for storage and analysis

**Environment Labels:** Uses common application variables from [infrastructure secrets](./secrets-infrastructure.md):
- `APP_NAME`, `APP_VERSION`
- `REGION`, `CLUSTER_ID`, `DEPLOYMENT_ENV`

## Architecture

The deployment includes three OTEL Collector instances:
- **Gateway**: Entry point for external telemetry data
- **API Server**: Collects metrics from Kubernetes API server
- **Backend**: Processes traces with tail sampling

## Security Notes

- Uses OpenObserve credentials for authentication to the data destination
- Ensure OpenObserve is deployed before the OTEL Collector
- Credentials are stored in Kubernetes secrets and used for API authentication
- Monitor authentication failures and credential rotation

## Deployment Order

1. [OpenObserve](./secrets-openobserve.md) (provides the data destination)
2. OTEL Collector (sends data to OpenObserve)
3. [Grafana](./secrets-grafana.md) (visualizes the collected data)

## Troubleshooting

- Check OpenObserve connectivity and authentication
- Verify environment variables are properly set
- Review component logs for authentication errors
- Ensure network policies allow communication between collector instances

## Related Documentation

- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements
- [OpenObserve Secrets](./secrets-openobserve.md) - Required data destination