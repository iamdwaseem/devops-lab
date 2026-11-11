# Experiment 13 — Terraform and Its Configurations

**Aim:** Use Terraform to create, validate, inspect and destroy a local resource.

## `main.tf` — version from the Terraform record

```hcl
terraform {
  required_providers {
    local = {
      source  = "hashicorp/local"
      version = "~> 2.5"
    }
  }
}

provider "local" {}

resource "local_file" "devops_file" {
  filename = "devops.txt"
  content  = "Infrastructure as Code using Terraform"
}
```

## Commands

```bash
terraform init
terraform validate
terraform plan
terraform apply
```

Type `yes` when prompted.

Verify:

```bash
cat devops.txt
terraform show
terraform state list
```

Expected resource address:

```text
local_file.devops_file
```

Cleanup:

```bash
terraform destroy
```

Type `yes`. The file is removed.

## Alternate uploaded-record configuration
Another copy of the record uses resource `local_file.lab_file`, filename `23071A0523.txt`, and content containing `Terraform Lab Activity` and the roll number. Do not mix the resource names/file names between the two variants.

**Result:** Terraform initialized, validated, planned, applied, inspected and destroyed the local resource.

**Viva:** Terraform = Infrastructure as Code; provider = plugin; resource = managed object; state = record of managed infrastructure; `init` initializes, `plan` previews, `apply` executes, `destroy` removes.
