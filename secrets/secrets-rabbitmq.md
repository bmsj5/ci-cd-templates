# RabbitMQ Secrets Setup

This file contains secrets required for RabbitMQ deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## RabbitMQ Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` secret:

```json
{
  "RABBITMQ_DEFAULT_USER": "your-rabbitmq-username",
  "RABBITMQ_DEFAULT_PASS": "your-secure-rabbitmq-password"
}
```

## Usage

These credentials are used for:
- RabbitMQ management interface access
- Default administrative user for message broker operations
- Application connections to RabbitMQ

## Security Notes

- Use a strong, unique password for RabbitMQ access
- Consider creating separate virtual hosts and users for different applications
- The default user has administrative privileges - create restricted users for applications
- Rotate passwords regularly according to your security policy

## Virtual Hosts and Users

The deployment supports:
- Default virtual host (/)
- Administrative user (default credentials)
- Application-specific users with restricted permissions (configured per service)

## Related Documentation

- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements