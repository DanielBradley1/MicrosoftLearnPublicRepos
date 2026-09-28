<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementserviceprincipalconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-14 -->

# appManagementServicePrincipalConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration object to configure app management policy restrictions like password credentials and certificate key credentials that are specific to service principals.

Inherits from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| keyCredentials | [keyCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/keycredentialconfiguration?view=graph-rest-beta) collection | Collection of certificate credential restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-beta). |
| passwordCredentials | [passwordCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredentialconfiguration?view=graph-rest-beta) collection | Collection of password restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appManagementServicePrincipalConfiguration",
  "passwordCredentials": [
    {
      "@odata.type": "microsoft.graph.passwordCredentialConfiguration"
    }
  ],
  "keyCredentials": [
    {
      "@odata.type": "microsoft.graph.keyCredentialConfiguration"
    }
  ]
}
```
