# Terraform Backend

This repository bootstraps the remote backend used for Terraform state.

## Purpose

The backend is managed separately from workload infrastructure so that Terraform projects do not manage the system that stores their own state.

This repository creates:

- An S3 bucket for Terraform remote state
- Versioning on the state bucket
- Server-side encryption on the state bucket
- Public access block on the state bucket
- Bucket ownership controls
- A DynamoDB table for Terraform state locking

## Created Resources

- S3 bucket: `jake-terraform-state-318361291464-eu-west-2`
- DynamoDB table: `terraform-backend-locks`

## Outputs

- `terraform_state_bucket_name`
- `terraform_state_bucket_arn`
- `terraform_lock_table_name`

## Relationship to terraform-foundations

The `terraform-foundations` repository uses this backend to store and lock its Terraform state remotely.

This separation mirrors a more production-shaped Terraform setup, where backend infrastructure is bootstrapped independently from workload infrastructure.