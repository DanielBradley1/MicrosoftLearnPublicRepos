<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditactor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-23 -->

# cloudPcAuditActor resource type

Namespace: microsoft.graph

The audit actor represented by the Microsoft Entra user and application associated with the audit event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationDisplayName | String | Name of the application. |
| applicationId | String | Microsoft Entra application ID. |
| ipAddress | String | IP address. |
| remoteTenantId | String | The delegated partner tenant ID. |
| remoteUserId | String | The delegated partner user ID. |
| servicePrincipalName | String | Service Principal Name \(SPN\). |
| userId | String | Microsoft Entra user ID. |
| userPermissions | String collection | List of user permissions and application permissions when the audit event was performed. |
| userPrincipalName | String | User Principal Name \(UPN\). |
| userRoleScopeTags | [cloudPcUserRoleScopeTagInfo](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcuserrolescopetaginfo?view=graph-rest-1.0) collection | List of role scope tags. |

## Relationships

None.

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAuditActor",
  "userPermissions": [
    "String"
  ],
  "applicationId": "String",
  "applicationDisplayName": "String",
  "userPrincipalName": "String",
  "servicePrincipalName": "String",
  "ipAddress": "String",
  "userId": "String",
  "userRoleScopeTags": [
    {
      "@odata.type": "microsoft.graph.cloudPcUserRoleScopeTagInfo",
      "displayName": "String",
      "roleScopeTagId": "String"
    }
  ],
  "remoteTenantId": "String",
  "remoteUserId": "String"
}
```
