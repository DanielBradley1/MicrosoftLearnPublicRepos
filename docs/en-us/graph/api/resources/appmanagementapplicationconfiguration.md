<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementapplicationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# appManagementApplicationConfiguration resource type

Namespace: microsoft.graph

Configuration object to configure app management policy restrictions like identifier URIs, password credentials, and certificate credentials that are specific to applications.

Inherits from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierUris | [identifierUriConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identifieruriconfiguration?view=graph-rest-1.0) | Configuration object for restrictions on **identifierUris** property for an application. |
| keyCredentials | [keyCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/keycredentialconfiguration?view=graph-rest-1.0) collection | Collection of certificate credential restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0). |
| passwordCredentials | [passwordCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredentialconfiguration?view=graph-rest-1.0) collection | Collection of password restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appManagementApplicationConfiguration",
  "identifierUris": {
    "@odata.type": "microsoft.graph.identifierUriConfiguration"
  },
  "keyCredentials": [
    {
      "@odata.type": "microsoft.graph.keyCredentialConfiguration"
    }
  ],
  "passwordCredentials": [
    {
      "@odata.type": "microsoft.graph.passwordCredentialConfiguration"
    }
  ]
}
```
