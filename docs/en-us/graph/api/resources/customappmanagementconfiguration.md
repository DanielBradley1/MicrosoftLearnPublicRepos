<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# customAppManagementConfiguration resource type

Namespace: microsoft.graph

Configuration object that can be configured to enable various restrictions for applications and service principals as part of the [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) object. Some of these restrictions apply to both applications and service principals while others are applicable only to applications.

Inherits from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationRestrictions | [customAppManagementApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customappmanagementapplicationconfiguration?view=graph-rest-1.0) | Restrictions that are applicable only to application objects to which the policy is attached. |
| keyCredentials | [keyCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/keycredentialconfiguration?view=graph-rest-1.0) collection | Collection of keyCredential restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0). |
| passwordCredentials | [passwordCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredentialconfiguration?view=graph-rest-1.0) collection | Collection of password restrictions settings to be applied to an application or service principal. Inherited from [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAppManagementConfiguration",
  "applicationRestrictions": {
    "@odata.type": "microsoft.graph.customAppManagementApplicationConfiguration"
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
