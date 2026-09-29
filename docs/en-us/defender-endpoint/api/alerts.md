<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/alerts -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Alert resource type

For the full available Alerts API experience across all Microsoft Defenders' products, visit: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| ID | String | Alert ID. |
| title | String | Alert title. |
| description | String | Alert description. |
| alertCreationTime | Nullable DateTimeOffset | The date and time \(in UTC\) the alert was created. |
| lastEventTime | Nullable DateTimeOffset | The last occurrence of the event that triggered the alert on the same device. |
| firstEventTime | Nullable DateTimeOffset | The first occurrence of the event that triggered the alert on that device. |
| lastUpdateTime | Nullable DateTimeOffset | The date and time \(in UTC\) the alert was last updated. |
| resolvedTime | Nullable DateTimeOffset | The date and time in which the status of the alert was changed to *Resolved*. |
| incidentId | Nullable Long | The [Incident](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue) ID of the Alert. |
| investigationId | Nullable Long | The [Investigation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) ID related to the Alert. |
| investigationState | Nullable Enum | The current state of the [Investigation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations). Possible values are: *Unknown*, *Terminated*, *SuccessfullyRemediated*, *Benign*, *Failed*, *PartiallyRemediated*, *Running*, *PendingApproval*, *PendingResource*, *PartiallyInvestigated*, *TerminatedByUser*, *TerminatedBySystem*, *Queued*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *SuppressedAlert*. |
| assignedTo | String | Owner of the alert. |
| rbacGroupName | String | Role-based access control device group name. |
| mitreTechniques | String | Mitre Enterprise technique ID. |
| relatedUser | String | Details of user related to a specific alert. |
| severity | Enum | Severity of the alert. Possible values are: *UnSpecified*, *Informational*, *Low*, *Medium*, and *High*. |
| status | Enum | Specifies the current status of the alert. Possible values are: *Unknown*, *New*, *InProgress* and *Resolved*. |
| classification | Nullable Enum | Specification of the alert. Possible values are: `TruePositive`, `Informational, expected activity`, and `FalsePositive`. |
| determination | Nullable Enum | Specifies the determination of the alert.<br><br>Possible determination values for each classification are:  <br><br><br><li> <b>True positive</b>: <code>Multistage attack</code> (MultiStagedAttack), <code>Malicious user activity</code> (MaliciousUserActivity), <code>Compromised account</code> (CompromisedUser) – consider changing the enum name in public API accordingly, <code>Malware</code> (Malware), <code>Phishing</code> (Phishing), <code>Unwanted software</code> (UnwantedSoftware), and <code>Other</code> (Other). </li><br><br><li> <b>Informational, expected activity:</b> <code>Security test</code> (SecurityTesting), <code>Line-of-business application</code> (LineOfBusinessApplication), <code>Confirmed activity</code> (ConfirmedUserActivity) - consider changing the enum name in public API accordingly, and <code>Other</code> (Other). </li><br><br><li>  <b>False positive:</b> <code>Not malicious</code> (Clean) - consider changing the enum name in public API accordingly, <code>Not enough data to validate</code> (InsufficientData), and <code>Other</code> (Other).</li> |
| category | String | Category of the alert. |
| detectionSource | String | Detection source. |
| threatFamilyName | String | Threat family. |
| threatName | String | Threat name. |
| machineId | String | ID of a [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entity that is associated with the alert. |
| computerDnsName | String | [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) fully qualified name. |
| aadTenantId | String | The Microsoft Entra ID. |
| detectorId | String | The ID of the detector that triggered the alert. |
| comments | List of Alert comments | Alert Comment object contains: comment string, createdBy string, and createTime date time. |
| Evidence | List of Alert evidence | Evidence related to the alert. See the following example. |

Note

Around August 29, 2022, previously supported alert determination values \(*Apt* and *SecurityPersonnel*\) will be deprecated and no longer available via the API.

### Response example for getting single alert:

```http
GET https://api.security.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
{
    "id": "da637472900382838869_1364969609",
    "incidentId": 1126093,
    "investigationId": null,
    "assignedTo": null,
    "severity": "Low",
    "status": "New",
    "classification": null,
    "determination": null,
    "investigationState": "Queued",
    "detectionSource": "WindowsDefenderAtp",
    "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
    "category": "Execution",
    "threatFamilyName": null,
    "title": "Low-reputation arbitrary code executed by signed executable",
    "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
    "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
    "firstEventTime": "2021-01-26T20:31:32.9562661Z",
    "lastEventTime": "2021-01-26T20:31:33.0577322Z",
    "lastUpdateTime": "2021-01-26T20:33:59.2Z",
    "resolvedTime": null,
    "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
    "computerDnsName": "temp123.middleeast.corp.microsoft.com",
    "rbacGroupName": "A",
    "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
    "threatName": null,
    "mitreTechniques": [
        "T1064",
        "T1085",
        "T1220"
    ],
    "relatedUser": {
        "userName": "temp123",
        "domainName": "DOMAIN"
    },
    "comments": [
        {
            "comment": "test comment for docs",
            "createdBy": "secop123@contoso.com",
            "createdTime": "2021-01-26T01:00:37.8404534Z"
        }
    ],
    "evidence": [
        {
            "entityType": "User",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": null,
            "sha256": null,
            "fileName": null,
            "filePath": null,
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": "name",
            "domainName": "DOMAIN",
            "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
            "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
            "userPrincipalName": "temp123@microsoft.com",
            "detectionStatus": null
        },
        {
            "entityType": "Process",
            "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
            "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
            "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
            "fileName": "rundll32.exe",
            "filePath": "C:\\Windows\\SysWOW64",
            "processId": 3276,
            "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
            "processCreationTime": "2021-01-26T20:31:32.9581596Z",
            "parentProcessId": 8420,
            "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
            "parentProcessFileName": "rundll32.exe",
            "parentProcessFilePath": "C:\\Windows\\System32",
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        },
        {
            "entityType": "File",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
            "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
            "fileName": "suspicious.dll",
            "filePath": "c:\\temp",
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        }
    ]
}
```
