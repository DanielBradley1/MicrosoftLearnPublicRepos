<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# automatedActionSet resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the automated response actions grouped by target entity type in the **automatedActions** property of a [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) for a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta). Each collection identifies the hunting-query output columns used to locate the impacted devices, files, accounts, or email messages for the action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowFiles | [microsoft.graph.security.fileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-fileaction?view=graph-rest-beta) collection | File actions that allow files identified by file hash columns in the hunting-query results. |
| blockFiles | [microsoft.graph.security.fileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-fileaction?view=graph-rest-beta) collection | File actions that block files identified by file hash columns in the hunting-query results. |
| collectInvestigationPackages | [microsoft.graph.security.deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta) collection | Device actions that collect investigation packages from devices identified in the hunting-query results. |
| disableUsers | [microsoft.graph.security.accountSidAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountsidaction?view=graph-rest-beta) collection | Account actions that disable users identified by account SID columns in the hunting-query results. |
| forceUserPasswordResets | [microsoft.graph.security.accountSidAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountsidaction?view=graph-rest-beta) collection | Account actions that force password resets for users identified by account SID columns in the hunting-query results. |
| hardDeleteEmails | [microsoft.graph.security.emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta) collection | Email actions that permanently delete messages identified in the hunting-query results. |
| initiateInvestigations | [microsoft.graph.security.deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta) collection | Device actions that initiate investigations on devices identified in the hunting-query results. |
| isolateDevices | [microsoft.graph.security.isolateDeviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceaction?view=graph-rest-beta) collection | Device actions that isolate devices identified in the hunting-query results. |
| markUsersAsCompromised | [microsoft.graph.security.accountObjectIdAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountobjectidaction?view=graph-rest-beta) collection | Account actions that mark users as compromised when they're identified by Microsoft Entra object ID columns in the hunting-query results. |
| moveEmailsToDeletedItems | [microsoft.graph.security.emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta) collection | Email actions that move messages identified in the hunting-query results to Deleted Items. |
| moveEmailsToInbox | [microsoft.graph.security.emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta) collection | Email actions that move messages identified in the hunting-query results to the Inbox. |
| moveEmailsToJunk | [microsoft.graph.security.emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta) collection | Email actions that move messages identified in the hunting-query results to Junk Email. |
| restrictAppExecutions | [microsoft.graph.security.deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta) collection | Device actions that restrict app execution on devices identified in the hunting-query results. |
| runAntivirusScans | [microsoft.graph.security.deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta) collection | Device actions that run antivirus scans on devices identified in the hunting-query results. |
| softDeleteEmails | [microsoft.graph.security.emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta) collection | Email actions that soft-delete messages identified in the hunting-query results. |
| stopAndQuarantineFiles | [microsoft.graph.security.stopAndQuarantineFileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileaction?view=graph-rest-beta) collection | File actions that stop running files and quarantine them on devices identified in the hunting-query results. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.automatedActionSet",
  "allowFiles": [
    {
      "@odata.type": "microsoft.graph.security.fileAction"
    }
  ],
  "blockFiles": [
    {
      "@odata.type": "microsoft.graph.security.fileAction"
    }
  ],
  "collectInvestigationPackages": [
    {
      "@odata.type": "microsoft.graph.security.deviceAction"
    }
  ],
  "disableUsers": [
    {
      "@odata.type": "microsoft.graph.security.accountSidAction"
    }
  ],
  "forceUserPasswordResets": [
    {
      "@odata.type": "microsoft.graph.security.accountSidAction"
    }
  ],
  "hardDeleteEmails": [
    {
      "@odata.type": "microsoft.graph.security.emailAction"
    }
  ],
  "initiateInvestigations": [
    {
      "@odata.type": "microsoft.graph.security.deviceAction"
    }
  ],
  "isolateDevices": [
    {
      "@odata.type": "microsoft.graph.security.isolateDeviceAction"
    }
  ],
  "markUsersAsCompromised": [
    {
      "@odata.type": "microsoft.graph.security.accountObjectIdAction"
    }
  ],
  "moveEmailsToDeletedItems": [
    {
      "@odata.type": "microsoft.graph.security.emailAction"
    }
  ],
  "moveEmailsToInbox": [
    {
      "@odata.type": "microsoft.graph.security.emailAction"
    }
  ],
  "moveEmailsToJunk": [
    {
      "@odata.type": "microsoft.graph.security.emailAction"
    }
  ],
  "restrictAppExecutions": [
    {
      "@odata.type": "microsoft.graph.security.deviceAction"
    }
  ],
  "runAntivirusScans": [
    {
      "@odata.type": "microsoft.graph.security.deviceAction"
    }
  ],
  "softDeleteEmails": [
    {
      "@odata.type": "microsoft.graph.security.emailAction"
    }
  ],
  "stopAndQuarantineFiles": [
    {
      "@odata.type": "microsoft.graph.security.stopAndQuarantineFileAction"
    }
  ]
}
```
