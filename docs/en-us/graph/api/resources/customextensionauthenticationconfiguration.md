<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# customExtensionAuthenticationConfiguration resource type

Namespace: microsoft.graph

Abstract base type that exposes the configuration for the **authenticationConfiguration** property of the derived types that inherit from the [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0) abstract type.

This abstract type is inherited by the following resource types:

- [azureAdTokenAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadtokenauthentication?view=graph-rest-1.0)
- [azureAdPopTokenAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadpoptokenauthentication?view=graph-rest-1.0)

The type of token authentication used depends on the token security. If the token security value is normal, you use the [azureAdTokenAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadtokenauthentication?view=graph-rest-1.0) resource type. If the value is Proof of Possession, you use the [azureAdPopTokenAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadpoptokenauthentication?view=graph-rest-1.0) resource type.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{ 
  "@odata.type": "#microsoft.graph.customExtensionAuthenticationConfiguration" 
} 
```
