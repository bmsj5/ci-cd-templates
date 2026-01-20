# MongoDB Secrets Setup

This file contains secrets required for MongoDB deployment and configuration.

## Configuration

**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)

## MongoDB Secrets (Via ANSIBLE_EXTRA_SECRETS_JSON)

Add these secrets to the `ANSIBLE_EXTRA_SECRETS_JSON` secret:

```json
{
  "MONGO_INITDB_ROOT_PASSWORD": "your-secure-mongodb-admin-password"
}
```

## Usage

This password is used for:
- MongoDB root/admin user authentication
- Database administration and management
- Initial database setup and configuration

## Security Notes

- Use a strong, unique password for MongoDB admin access
- This password provides full administrative access to all databases
- Consider creating separate application users with limited privileges for production
- Rotate passwords regularly according to your security policy

## Database Users

The deployment creates:
- Root admin user with full access
- Application-specific users with restricted permissions (configured per service)

## Related Documentation

- [Infrastructure Secrets](./secrets-infrastructure.md) - Infrastructure-level requirements