# Extra Topic 4 — Terraform Configuration Execution and State Management

**Aim:** Execute Terraform configuration and understand the state file.

## Minimal configuration

```hcl
terraform {
  required_providers {
    local = {
      source = "hashicorp/local"
    }
  }
}

resource "local_file" "demo" {
  filename = "${path.module}/demo.txt"
  content  = "Terraform state demo"
}
```

## Lifecycle

```bash
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
terraform show
terraform state list
```

After apply, Terraform creates `terraform.tfstate` locally (unless using a configured remote backend).

Useful state commands:

```bash
terraform state list
terraform state show local_file.demo
terraform state pull
```

Destroy:

```bash
terraform destroy
```

## Key concepts
- State maps Terraform configuration resources to real objects and records attributes.
- Do not manually edit state files.
- For team use, configure a remote backend with locking and access control.
- Keep state files and secrets out of Git; add `*.tfstate*` and `.terraform/` to `.gitignore`.

**Viva:** State tracks resources; backend stores state; locking prevents concurrent state modifications; drift is a difference between real infrastructure and configuration/state.
