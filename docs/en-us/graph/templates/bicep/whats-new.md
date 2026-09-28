<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/whats-new -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# What's new in Bicep templates for Microsoft Graph?

This article summarizes recent documentation and feature updates for Microsoft Graph Bicep templates. For more announcements, community discussions, and support, see the [Microsoft Graph Bicep types GitHub repository](https://github.com/microsoftgraph/msgraph-bicep-types/issues).

## July 2025

- Microsoft Graph Bicep is now generally available and supported in production environments, following the [Microsoft APIs terms of use](https://learn.microsoft.com/en-us/legal/microsoft-apis/terms-of-use).

  - Microsoft Graph Bicep types [v1.0.0 release](https://github.com/microsoftgraph/msgraph-bicep-types/releases/tag/v1.0.0) which has the `br:mcr.microsoft.com/bicep/extensions/microsoftgraph/v1.0:1.0.0` type version.
  - Minimum required Bicep version: [v0.36.1](https://github.com/Azure/bicep/releases/tag/v0.36.1).

- Debug logging is now supported. First [enable debug logging](https://learn.microsoft.com/en-us/azure/azure-resource-manager/troubleshooting/enable-debug-logging?tabs=azure-powershell#set-up-debug-logging) using Azure PowerShell and then use the [Azure CLI deployment operations command](https://learn.microsoft.com/en-us/azure/azure-resource-manager/troubleshooting/enable-debug-logging?tabs=azure-cli#set-up-debug-logging) to see debug information with the Microsoft Graph `request` and `response` properties.
- Stream properties, like `logo` on the `applications` resource, are now supported. [Create a client application with a logo](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/create-client-app-with-logo) demonstrates how to binary logo file as a stream property of an application.
- Creating your own client application to deploy Microsoft Graph resources interactively \(using the user on-behalf-of flow\) is now supported. Try out this [dotnet command-line template deployment sample app](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/samples/deploy-template) available in GitHub.

## March 2025

- **Warning**: The built-in Bicep extension for Microsoft Graph is retired. Only [dynamic types](https://learn.microsoft.com/en-us/graph/templates/bicep/how-to-dynamic-types) are supported. All samples and quickstarts now use dynamic types.
- The Microsoft Graph Bicep types [v0.2.0-preview release](https://github.com/microsoftgraph/msgraph-bicep-types/releases/tag/v0.2.0-preview) includes:

  - Enhanced relationship management \(such as `members` and `owners`\) for adding or removing any number of items. Template authors can choose between append \(default\) or replace semantics. For details, see the [Configure a security group's user members, using user principal names](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-add-user-members) sample and the [modeling relationships in Microsoft Graph Bicep types](https://learn.microsoft.com/en-us/graph/templates/bicep/concept-relationships-in-graph-types) article.
  - Support for setting the `owners` relationship on both `applications` and `servicePrincipals`.
  - Ability to output all relationship arrays, as shown in the [Configure a security group's user members, using user principal names](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-add-user-members) sample.

## January 2025

- Bicep templates for Microsoft Graph now support [national clouds](https://learn.microsoft.com/en-us/graph/templates/bicep/overview-bicep-templates-for-graph#national-cloud-support).
- Introduced the read-only `users` Bicep type for [beta](https://learn.microsoft.com/en-us/graph/templates/bicep/reference/users) and [v1.0](https://learn.microsoft.com/en-us/graph/templates/bicep/reference/users) with the Microsoft Graph Bicep types [v0.1.9-preview release](https://github.com/microsoftgraph/msgraph-bicep-types/releases/tag/v0.1.9-preview). See the [Configure a security group's user members, using user principal names](https://github.com/microsoftgraph/msgraph-bicep-types/tree/main/quickstart-templates/security-group-add-user-members) sample for usage.
