# Infrastructure Secrets Setup

This file contains secrets and variables required for infrastructure-level deployments and common across all services.

## Configuration

**Repository Secrets**: Set directly in GitHub repository secrets  
**Repository Variables**: Set directly in GitHub repository variables  
**JSON Secrets**: Add to `ANSIBLE_EXTRA_SECRETS_JSON` secret (JSON format)  
**JSON Variables**: Add to `ANSIBLE_EXTRA_ENV_JSON` variable (JSON format)

## Infrastructure Secrets (Set Directly in GitHub)

These secrets are used by the Ansible playbooks for connecting to and managing the Kubernetes cluster:

```
ANSIBLE_HOSTS          - Comma-separated k3s server IPs/hostnames
SSH_PRIVATE_KEY        - SSH private key for connecting to k3s servers
KUBECONFIG             - Kubernetes configuration for cluster access
```

## Infrastructure Variables (Set Directly in GitHub)

```
AUTO_DEPLOY=true/false  - Whether to enable automatic deployments
```

## Common Application Variables (Via ANSIBLE_EXTRA_ENV_JSON)

These variables are shared across multiple services and go into a single JSON variable `ANSIBLE_EXTRA_ENV_JSON`:

```json
{
  "APP_NAME": "your-app-name",
  "APP_VERSION": "1.0.0",
  "REGION": "eu-east-1",
  "CLUSTER_ID": "your-cluster-id",
  "DEPLOYMENT_ENV": "production"
}
```

### Usage Notes

- `APP_NAME`: Application name for labeling and identification
- `APP_VERSION`: Application version for tracking and rollbacks
- `REGION`: Used for resource tagging and multi-region deployments
- `CLUSTER_ID`: Unique identifier for the Kubernetes cluster
- `DEPLOYMENT_ENV`: Environment identifier (production/staging/dev)

## Related Documentation

- [Main Secrets Setup](../SECRETS_SETUP.md) - Overview of all secret configurations
- [Component-specific secrets](./) - Individual service secret requirements