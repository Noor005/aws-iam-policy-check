# AWS IAM Policy Check with Terraform and GitHub Actions

This cloud security lab uses Checkov to scan a Terraform-defined AWS IAM
policy for overly broad S3 permissions. The GitHub Actions workflow runs
on pushes and pull requests.

## What I tested

| Test | IAM permission | Result |
|---|---|---|
| Before | `s3:GetObject` with `Resource = "*"` | Checkov flagged the policy under rule `CKV_AWS_355`. |
| After | `s3:GetObject` scoped to objects in one example S3 bucket | The GitHub Actions workflow succeeded. |

The workflow scanned the Terraform source before deployment. The lab
required no AWS credentials or deployed resources.
