# Terraform CI validation

[![Terraform Validation](https://github.com/alwinfranc1s/ci-validation-terraform/actions/workflows/terraform-validation.yml/badge.svg?branch=main)](https://github.com/alwinfranc1s/ci-validation-terraform/actions/workflows/terraform-validation.yml)

This beginner-friendly project shows how to check Terraform configuration with
GitHub Actions. It configures the AWS provider and exposes the configured region
as an output, but does not define or deploy any AWS resources. The checks do not
require AWS credentials.

## GitHub Actions

The Terraform Validation workflow runs on pushes to `main` and pull requests
targeting `main`. It checks out the repository, installs Terraform, checks
formatting, initializes providers without a backend, and validates the
configuration. It does not run `terraform plan` or `terraform apply`.

## Run the checks locally

Install [Terraform](https://developer.hashicorp.com/terraform/install), then run
these commands from the repository root:

```sh
terraform fmt -check -recursive
terraform init -backend=false
terraform validate
```

Initialization downloads the AWS provider, so it requires internet access.
If the formatting check fails, run `terraform fmt -recursive` to fix it.
