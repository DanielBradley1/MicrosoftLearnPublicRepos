<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# appIdentity resource type

Namespace: microsoft.graph

Indicates the identity of the application that performed the action or was changed. Includes the application ID, name, and service principal ID and name. This object is configured in the **app** property of [auditActivityInitiator](https://learn.microsoft.com/en-us/graph/api/resources/auditactivityinitiator?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Refers to the unique ID representing application in Microsoft Entra ID. |
| displayName | String | Refers to the application name displayed in the Microsoft Entra admin center. |
| servicePrincipalId | String | Refers to the unique ID for the service principal in Microsoft Entra ID. |
| servicePrincipalName | String | Refers to the Service Principal Name is the Application name in the tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appId": "String",
  "displayName": "String",
  "servicePrincipalId": "String",
  "servicePrincipalName": "String"
}
```
