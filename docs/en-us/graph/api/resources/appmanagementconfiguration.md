<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-14 -->

# appManagementConfiguration resource type

Namespace: microsoft.graph

App management configuration object that contains properties which can be configured to enable various restrictions for applications and service principals.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| passwordCredentials | [passwordCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredentialconfiguration?view=graph-rest-1.0) collection | Collection of password restrictions settings to be applied to an application or service principal. |
| keyCredentials | [keyCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/keycredentialconfiguration?view=graph-rest-1.0) collection | Collection of keyCredential restrictions settings to be applied to an application or service principal. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appManagementConfiguration",
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
