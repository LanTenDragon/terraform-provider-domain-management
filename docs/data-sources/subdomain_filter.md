---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "st-domain-management_subdomain_filter Data Source - terraform-provider-st-domain-management"
subcategory: ""
description: |-
  Query subdomains that satisfy the filter using Terraform Data Source.
---

# st-domain-management_subdomain_filter (Data Source)

Query subdomains that satisfy the filter using Terraform Data Source.

## Example Usage

```terraform
data "st-domain-management_subdomain_filter" "example" {
  domain_labels = jsonencode({
    "common/brand" = "brand-A"
    "common/status" = "new"
    "common/project" = "project-B"
  })
  subdomain_labels = jsonencode({
    "module-specific-label/labelA" = true
    "module-specific-label/labelB" = ["a", "b", "c"]
  })
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `domain_labels` (String) Domain labels filter. Only domains that contain these labels will be returned as data source output.
- `subdomain_labels` (String) Subdomain labels filter. Only subdomains that contain these labels will be returned as data source output

### Optional

- `domain_annotations` (String) Annotations filter. Only domains that contain these annotations will be returned as data source output.

### Read-Only

- `domains` (Attributes Set) (see [below for nested schema](#nestedatt--domains))

<a id="nestedatt--domains"></a>
### Nested Schema for `domains`

Read-Only:

- `domain` (String) The main domain of this result.
- `subdomains` (Attributes Set) (see [below for nested schema](#nestedatt--domains--subdomains))

<a id="nestedatt--domains--subdomains"></a>
### Nested Schema for `domains.subdomains`

Read-Only:

- `fqdn` (String) The result of joining the subdomain name with the main domain.
- `labels` (String) The JSON encoded string of the labels attachd to this subdomain. Wrap this resource in jsonencode() to use it as a Terraform resource.
- `name` (String) The name of subdomain.
