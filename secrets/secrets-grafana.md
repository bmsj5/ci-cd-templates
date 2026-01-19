# Grafana Secrets Setup

This file contains secrets required for Grafana deployment and configuration.

## Grafana Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` variable:

```json
{
  "GRAFANA_ADMIN_USER": "admin",
  "GRAFANA_ADMIN_PASSWORD": "your-secure-admin-password",
  "GRAFANA_DB_PASSWORD": "your-secure-db-password"
}
```

## Usage

These credentials are used for:

- **GRAFANA_ADMIN_USER**: Grafana web UI administrator username
- **GRAFANA_ADMIN_PASSWORD**: Grafana web UI administrator password
- **GRAFANA_DB_PASSWORD**: Password for Grafana's PostgreSQL database connection

## OpenObserve Integration

Grafana also uses OpenObserve credentials for data source configuration. Make sure you have configured [OpenObserve secrets](./secrets-openobserve.md):

```json
{
  "ZO_ROOT_USER_EMAIL": "admin@yourdomain.com",
  "ZO_ROOT_USER_PASSWORD": "your-secure-password"
}
```

## Security Notes

- Use strong, unique passwords for admin access
- Consider using a non-default admin username
- The database password should be different from the admin password
- Rotate passwords regularly according to your security policy

## Data Sources

Grafana is pre-configured to connect to:
- OpenObserve (for logs, metrics, traces)
- PostgreSQL (for Grafana's internal database)
- Victoria Metrics (for metrics)
- Tempo (for traces)

## Related Documentation

- [Main Secrets Setup](../SECRETS_SETUP.md) - Overview of all secret configurations
- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements
- [OpenObserve Secrets](./secrets-openobserve.md) - Required for data source integration