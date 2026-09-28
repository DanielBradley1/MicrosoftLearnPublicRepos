<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# synchronization resource type

Namespace: microsoft.graph

Represents the capability for Microsoft Entra identity synchronization through the Microsoft Graph API. Identity synchronization \(also called *provisioning*\) allows you to automate the provisioning \(creation, maintenance\) and deprovisioning \(removal\) of user identities and roles from Microsoft Entra ID to supported cloud applications. For more information, see [How Application Provisioning works in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/how-provisioning-works)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Acquire access token](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronization-acquireaccesstoken?view=graph-rest-1.0) | None | Acquire an OAuth Access token to authorize the Microsoft Entra provisioning service to provision users into an application. |
| [Add secrets](https://learn.microsoft.com/en-us/graph/api/synchronization-serviceprincipal-put-synchronization?view=graph-rest-1.0) | None | Provide credentials for establishing connectivity with the target system. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| secrets | [synchronizationSecretKeyStringValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationsecretkeystringvaluepair?view=graph-rest-1.0) collection | Represents a collection of credentials to access provisioned cloud applications. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| jobs | [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) collection | Performs synchronization by periodically running in the background, polling for changes in one directory, and pushing them to another directory. |
| templates | [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) collection | Preconfigured synchronization settings for a particular application. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronization",
  "secrets": [
    {
      "@odata.type": "microsoft.graph.synchronizationSecretKeyStringValuePair"
    }
  ]
}
```
