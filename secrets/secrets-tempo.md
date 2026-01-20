# Tempo Secrets Setup

This file contains secrets required for Tempo (distributed tracing) deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## Tempo Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` variable:

```json
{
  "TEMPO_MINIO_ACCESS_KEY": "tempo-minio-user",
  "TEMPO_MINIO_SECRET_KEY": "your-secure-minio-secret-key"
}
```

## Usage

These credentials are used for:

- **TEMPO_MINIO_ACCESS_KEY**: MinIO S3-compatible storage access key for Tempo traces
- **TEMPO_MINIO_SECRET_KEY**: MinIO S3-compatible storage secret key for Tempo traces

## Storage Configuration

Tempo uses MinIO as its object storage backend for storing trace data. The deployment includes:

- MinIO server setup with the provided credentials
- Tempo configuration to use MinIO for trace storage
- S3-compatible API access for distributed trace storage

## Security Notes

- Use strong, unique credentials for MinIO access
- These credentials provide access to all stored trace data
- Rotate keys regularly according to your security policy
- Consider using IAM roles or temporary credentials in production

## Integration

Tempo traces are visualized in:
- [Grafana](./secrets-grafana.md) - for trace visualization
- OpenObserve - for correlated logs and traces

## Related Documentation

- [Main Secrets Setup](../SECRETS_SETUP.md) - Overview of all secret configurations
- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements