# Redis Secrets Setup

This file contains secrets required for Redis deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## Redis Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` secret:

```json
{
  "REDIS_PASSWORD": "your-secure-redis-password"
}
```

## Usage

This password is used for:
- Redis server authentication
- Client connections to Redis
- Redis cluster communication

## Security Notes

- Use a strong, unique password for Redis access
- This password provides full access to the Redis database
- Consider using Redis ACLs for fine-grained access control in production
- Rotate passwords regularly according to your security policy

## Related Documentation

- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements