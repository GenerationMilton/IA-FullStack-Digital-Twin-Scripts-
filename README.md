To create a specific environment:

Mac/Linux:

```bash
./scripts/deploy.sh test
./scripts/deploy.sh dev
./scripts/deploy.sh prod
```

Windows (PowerShell):

```bash
.\scripts\deploy.ps1 -Environment test
.\scripts\deploy.ps1 -Environment dev
.\scripts\deploy.ps1 -Environment prod 
```


```
chmod +x scripts/destroy.sh
```

To destroy a specific environment:

Mac/Linux:

```bash
# Destroy dev environment
./scripts/destroy.sh dev

# Destroy test environment
./scripts/destroy.sh test

# Destroy prod environment
./scripts/destroy.sh prod
```

Windows (PowerShell):

```bash
# Destroy dev environment
.\scripts\destroy.ps1 -Environment dev

# Destroy test environment
.\scripts\destroy.ps1 -Environment test

# Destroy prod environment
.\scripts\destroy.ps1 -Environment prod
```

## What Gets Destroyed

The destroy scripts will:

Empty S3 buckets (frontend and memory)
Delete all AWS resources created by Terraform:
Lambda functions
API Gateway
S3 buckets
CloudFront distributions
IAM roles and policies
Route 53 records (if custom domain)
ACM certificates (if custom domain)
## Important Notes

CloudFront: Distributions can take 5-15 minutes to fully delete
Workspaces: The scripts destroy resources but keep the workspace. To fully remove a workspace:

terraform workspace select default
terraform workspace delete dev  # or test, prod


Cost Savings: Always destroy unused environments to avoid charges