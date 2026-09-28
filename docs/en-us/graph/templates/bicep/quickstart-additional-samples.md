<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-additional-samples -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Additional Bicep samples on GitHub

The following samples on GitHub demonstrate different scenarios for deploying various Microsoft Graph Bicep types and configurations.

## Samples from the msgraph-bicep-types repo

You can also contribute to this collection of samples. For more information, see [Contributing to the Microsoft Graph Bicep Extension](https://github.com/microsoftgraph/msgraph-bicep-types/blob/main/CONTRIBUTING.md).

| Sample | Sample summary |
| --- | --- |
| [Create client and resource apps](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/application-serviceprincipal-create-client-resource) | <li> Create a client app registration with an optional X509 certificate </li><br><br><li> Create a resource app registration </li><br><br><li> Create service principals for both apps</li> |
| [Create a client app with an X509 certificate from Key Vault](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/create-client-app-sp-with-kv-cert) | <li> Create a client app registration </li><br><br><li> Add an X509 certificate from Key Vault using a deployment script </li><br><br><li> Create a service principal for the app</li> |
| [Create a client app with a logo](https://github.com/microsoftgraph/msgraph-bicep-types//tree/main/quickstart-templates/create-client-app-with-logo) | Create a client app registration with a logo demonstrating how to update a stream property. |
| [Configure a client app with OAuth2.0 scopes to call Microsoft Graph](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/apps-permissions-and-grants) | Create a client application and either:<br><br><li> Set required resource access on the client app definition, or </li><br><br><li> Grant OAuth2.0 scopes to the client application.</li> |
| [Configure GitHub Actions to access Azure resources, using zero secrets](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/create-fic-for-github-actions) | Enable a GitHub Action to log into Microsoft Entra, build and deploy a web app into an Azure App Service, without using any secrets.<br><br><li> Create a secret-less app configured with a federated identity credential for GitHub </li><br><br><li> Create a service principal and assign it a resource group scoped Azure Contributor role</li> |
| [Configure an app with a user-assigned managed identity as a credential](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/msi-as-a-fic-secretless) | Enable an app running in Azure to call Microsoft Graph API, without using any secrets<br><br><li> Create a secret-less client application, using a user-assigned managed identity as the credential </li><br><br><li> Create a service principal and assign it Microsoft Graph app roles </li><br><br><li> Assign the managed identity to an Azure Automation account, enabling the app to call Microsoft Graph</li> |
| [Grant a client app access to a resource app](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/resource-application-access-grant-to-client-application) | Create an app role assignment for the client app to the resource app that were created in [Create client and resource apps](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/application-serviceprincipal-create-client-resource) |
| [Enable a client service to read from Blob storage, using a security group](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-assign-azure-role) | Configure three user-assigned managed identities to read from a Blob Storage account via a security group:<br><br><li> Create 3 managed identities and add them as members of a security group </li><br><br><li> Assign an Azure Reader role to the Blob Storage account for the security group</li> |
| [Configure a security group's user members, using user principal names](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-add-user-members) | <li> Fetch users by UPN </li><br><br><li> Create a security group </li><br><br><li> Add the fetched users as members of the group</li> |
| [Create a group with members and owners](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-create-with-owners-and-members) | <li> Create a security group and: </li><br><br><li> Add a resource service principal as owner </li><br><br><li> Add a managed identity as member</li> |

## Samples from the Azure-Samples repo

These samples represent more complete end-to-end samples that integrate the use of Microsoft Graph Bicep types into Azure infrastructure deployment scenarios.

| Sample | Sample summary |
| --- | --- |
| [Built-in Auth for Azure App Service with Microsoft Entra ID](https://github.com/Azure-Samples/appservice-builtinauth-bicep) | Provision an Azure App Service app with the [built-in authentication feature](https://learn.microsoft.com/en-us/azure/app-service/overview-authentication-authorization) and a Microsoft Entra ID identity provider. The Bicep files use the Microsoft Graph Bicep extension to create the Entra application registration using [managed identity with Federated Identity Credentials](https://learn.microsoft.com/en-us/azure/app-service/overview-managed-identity), so that no client secrets or certificates are necessary. |
| [Built-in Auth for Azure Container Apps with Microsoft Entra ID](https://github.com/Azure-Samples/containerapps-builtinauth-bicep) | Provision an Azure Container App with the [built-in authentication feature](https://learn.microsoft.com/en-us/azure/container-apps/authentication) and a Microsoft Entra ID identity provider. The Bicep files use the Microsoft Graph Bicep extension to create the Entra application registration using [managed identity with Federated Identity Credentials](https://learn.microsoft.com/en-us/azure/app-service/overview-managed-identity), so that no client secrets or certificates are necessary. |
