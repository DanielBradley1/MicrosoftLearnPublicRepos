<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-06 -->

# backupRestoreRoot resource type

Namespace: microsoft.graph

Represents the Microsoft 365 Backup Storage service in a tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-get?view=graph-rest-1.0) | [backupRestoreRoot](https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot?view=graph-rest-1.0) | Get details of the Backup Storage service. |
| [Enable](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-enable?view=graph-rest-1.0) | [backupRestoreRoot](https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot?view=graph-rest-1.0) | Enable the Backup Storage service. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the Backup Storage service. |
| serviceStatus | [serviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/servicestatus?view=graph-rest-1.0) | Represents the tenant-level status of the Backup Storage service. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| browseSessions | [browseSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0) collection | The list of browse sessions in the tenant. |
| driveInclusionRules | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) collection | The list of drive inclusion rules applied to the tenant. |
| driveProtectionUnits | [driveProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0) collection | The list of drive protection units in the tenant. |
| emailNotificationsSetting | [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) | The email notification settings in the tenant. |
| exchangeProtectionPolicies | [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) collection | The list of Exchange protection policies in the tenant. |
| exchangeRestoreSessions | [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) collection | The list of Exchange restore sessions available in the tenant. |
| mailboxInclusionRules | [mailboxProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionrule?view=graph-rest-1.0) collection | The list of mailbox inclusion rules applied to the tenant. |
| mailboxProtectionUnits | [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0) collection | The list of mailbox protection units in the tenant. |
| oneDriveForBusinessBrowseSessions | [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0) collection | The list of OneDrive for Business browse sessions in the tenant. |
| oneDriveForBusinessProtectionPolicies | [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) collection | The list of OneDrive for Business protection policies in the tenant. |
| oneDriveForBusinessRestoreSessions | [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) collection | The list of OneDrive for Business restore sessions available in the tenant. |
| protectionPolicies | [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) collection | List of protection policies in the tenant. |
| protectionUnits | [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) collection | List of protection units in the tenant. |
| restorePoints | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) collection | List of restore points in the tenant. |
| restoreSessions | [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) collection | List of restore sessions in the tenant. |
| serviceApps | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) collection | List of Backup Storage apps in the tenant. |
| sharePointBrowseSessions | [sharePointBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointbrowsesession?view=graph-rest-1.0) collection | The list of SharePoint browse sessions in the tenant. |
| sharePointProtectionPolicies | [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) collection | The list of SharePoint protection policies in the tenant. |
| sharePointRestoreSessions | [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) collection | The list of SharePoint restore sessions available in the tenant. |
| siteInclusionRules | [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) collection | The list of site inclusion rules applied to the tenant. |
| siteProtectionUnits | [siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0) collection | The list of site protection units in the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.backupRestoreRoot",
  "id": "String (identifier)",
  "serviceStatus": {
    "@odata.type": "microsoft.graph.serviceStatus"
  }
}
```
