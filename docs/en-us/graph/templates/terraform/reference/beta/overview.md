<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/overview -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Terraform Microsoft Graph provider resource reference overview

Welcome to the reference for Terraform Microsoft Graph provider resources on the beta endpoint.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The `msgraph` provider for Terraform is currently in PREVIEW. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability.

## Supported resources

The following Terraform Microsoft Graph provider types are available for use in your Terraform files.

| Service | Terraform Microsoft Graph provider resource type |
| --- | --- |
| Applications | [applications](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/applications) |
| App role assignments | [appRoleAssignedTo](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/approleassignedto) |
| Federated identity credentials | [applications/federatedIdentityCredentials](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/federatedidentitycredentials) |
| Groups | [groups](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/groups) |
| OAuth2 permission grants \(delegated permission grants\) | [oauth2PermissionGrants](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/oauth2permissiongrants) |
| Service principals | [servicePrincipals](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/serviceprincipals) |
| Users | [users](https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/users) |

## Report functionality issues

To report bugs in the product, use the [GitHub issues forum](https://github.com/microsoft/terraform-provider-msgraph/issues).

## Feature requests

To submit feature requests, join the discussions with other developers on the [GitHub forum](https://github.com/microsoft/terraform-provider-msgraph/issues).
