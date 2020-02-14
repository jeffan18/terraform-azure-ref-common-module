

# Common Terraform Module - can use as a complete deployment

This modules is responsible for deploying the common stuff required for the reference archicture for Terraform on Azure. 

## Usage

```hcl
module "common-resources-module" {
  source                           = "../../"
  location                         = "useast"
  tenant_id                        = var.tenant_id
}
```

## Inputs

```hcl
variable "location" {
  description = "Azure location to use"
}

variable "tenant_id" {
  description = "The Azure tenant id"
}
```

## Outputs

```hcl
output "resource_group_name" {
  value = azurerm_resource_group.rg.name
}
```

## Run tests

### On your machine

*Note: You need to be authenticated to a valid Azure subscription (using Azure CLI).*

```bash
dep ensure -v
export TF_VAR_tenant_id="<YOUR_AZURE_TENANT_ID>"
go test -v ./test/ -timeout 20m
```
