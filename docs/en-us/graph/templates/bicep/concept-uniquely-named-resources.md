<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/concept-uniquely-named-resources -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Uniquely named resources for Bicep deployments

This article explains how unique resource keys differ between Microsoft Azure APIs and Microsoft Graph APIs. It also describes changes in Microsoft Graph APIs that support declarative infrastructure as code \(IaC\) templates, like Bicep files. You learn how to use unique resource keys to reference existing Microsoft Graph resources created outside Bicep deployments.

Important

Microsoft Graph Bicep is currently in PREVIEW. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to Azure features that are in beta, preview, or otherwise not yet released into general availability.

## Azure and Microsoft Graph resource keys

Microsoft Azure and Microsoft Graph APIs use different methods to create resources. This difference matters when you declare both types in the same Bicep template.

- **Azure APIs**: Use the HTTP PUT method with a client-provided unique key called `name`. This operation is idempotent - it creates the resource if it doesn't exist, or updates it if it does.

  ```http
  PUT /resourceCollection/{nameValue}
  ```

- **Microsoft Graph APIs**: Use the HTTP POST method, which isn't idempotent and returns a service-generated unique ID called `id`.

  ```http
  POST /resourceCollection
  ```

Updates in Microsoft Graph use the HTTP PATCH method, which doesn't replace the resource but updates its properties.

### Why this difference matters for Bicep

Declarative templates like Bicep require:

- **Repeatability**: Deployments should be idempotent, producing the same result every time. Most Microsoft Graph APIs use the HTTP POST method to create resources. This method isn't idempotent, so it's difficult to ensure repeatable deployments.
- **Client-provided keys**: You must declare resource names or keys up front. Most Microsoft Graph APIs don't support client-provided keys, so repeatable deployments are challenging.

## Microsoft Graph client-provided keys

Some Microsoft Graph resources support a client-provided key property. This property lets you perform idempotent upsert operations - create the resource if it isn't present, or update it if it exists. This key is often an alternate key, but sometimes it's the primary key.

```http
PATCH /resourceCollection(clientProvidedAlternateKeyProperty='nameValue')
```

When you create a resource this way, Microsoft Graph sets the primary key property.

Only resources that support this pattern are available as Microsoft Graph Bicep types, with few exceptions.

### Supported client-provided key properties

| Microsoft Graph resource | Client-provided key property |
| --- | --- |
| Applications | **uniqueName** |
| Federated identity credentials | **name** |
| App role assigned to | Implied from property values that uniquely identify the object |
| Groups | **uniqueName** |
| OAuth2 permission grants | Implied from property values that uniquely identify the object |
| Service principals | **appId** |
| Users | **userPrincipalName** |

## Referencing existing Microsoft Graph resources

Reference existing Microsoft Graph resources in Bicep templates by using the supported client-provided key property. Resources created with HTTP POST might not have this property set and can require a one-time update to backfill the property.

After you set the client-provided key, you can declare and redeploy the resource in Bicep. To read properties of an existing resource without redeploying, use the [existing](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/existing-resource) keyword.

Important

You can't change the client-provided key property after you set it.

## Next step

[Learn how to reference existing resources](https://learn.microsoft.com/en-us/graph/templates/bicep/how-to-reference-existing-resources)
