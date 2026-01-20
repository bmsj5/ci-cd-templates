# OpenObserve Secrets Setup

This file contains secrets required for OpenObserve deployment and integration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## OpenObserve Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` secret:

```json
{
  "ZO_ROOT_USER_EMAIL": "admin@yourdomain.com",
  "ZO_ROOT_USER_PASSWORD": "your-secure-password"
}
```

## Usage

These credentials are used for:

- **OpenObserve Web UI Access**: Root user login to the OpenObserve interface
- **API Authentication**: Used by other services (Grafana, OTEL Collector, Vector) to send data to OpenObserve
- **Data Ingestion**: Required for metrics, logs, and traces ingestion

## Security Notes

- Use a strong, unique password for the root user
- Consider using a service account email (e.g., `openobserve@yourdomain.com`)
- These credentials are shared with integrated services for data submission
- Rotate passwords regularly according to your security policy

## Related Services

These credentials are also used by:
- [Grafana](./secrets-grafana.md) - for data source configuration
- [OTEL Collector](./secrets-otel-collector.md) - for traces/metrics/logs export
- [Vector](./secrets-vector.md) - for log shipping

## Related Documentation

- [Main Secrets Setup](../SECRETS_SETUP.md) - Overview of all secret configurations
- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements