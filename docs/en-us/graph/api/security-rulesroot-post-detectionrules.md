<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-rulesroot-post-detectionrules?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# Create detectionRule

Namespace: microsoft.graph.security

Create a new [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomDetection.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomDetection.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a role that grants the permissions required for this operation. Custom detection rules use the Microsoft Defender XDR Unified role-based access control \(RBAC\) model. The following roles are supported:

- **Detection tuning \(Manage\)** - A [Microsoft Defender XDR Unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details) permission that grants manage access to detections in the Microsoft Defender portal, including custom detections, alert tuning, and threat indicators of compromise.
- **Security Administrator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-administrator) that grants manage permissions across Microsoft Defender portals and services.
- **Security Operator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-operator). Sufficient for managing custom detection rules only when role-based access control is turned off in Microsoft Defender for Endpoint. If RBAC is configured, the **Manage Security Settings** permission for Defender for Endpoint is also required.

Additional workload-specific permissions might be required to manage rules that target data from specific Defender workloads \(for example, Defender for Endpoint, Defender for Office 365\). For more information, see [Required permissions for managing custom detections](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules#required-permissions-for-managing-custom-detections).

## HTTP request

```http
POST /security/rules/detectionRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object.

You can specify the following properties and relationships when creating a **detectionRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A user-supplied description of the detection rule. Optional. |
| detectionAction | [microsoft.graph.security.detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-1.0) | The actions taken when a detection is made by this rule, including the alert that is created and any automated response actions. Required. |
| displayName | String | The display name of the rule. Required. |
| id | String | The client-provided unique identifier of the rule. Required. |
| queryCondition | [microsoft.graph.security.queryCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-1.0) | The advanced hunting query that defines the detection logic of this rule. Required. |
| schedule | [microsoft.graph.security.ruleSchedule](https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-1.0) | The triggering schedule of this rule. Required. |
| status | [microsoft.graph.security.detectionRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-1.0#detectionrulestatus-values) | The current run status of the rule. The possible values are: `enabled`, `disabled`, `autoDisabled`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/security/rules/detectionRules
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "office-encoded-powershell",
  "displayName": "Suspicious encoded PowerShell from Office",
  "description": "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
  "status": "enabled",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  },
  "schedule": {
    "frequency": "PT1H"
  },
  "detectionAction": {
    "alertTemplate": {
      "title": "Suspicious encoded PowerShell from Office",
      "description": "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
      "severity": "high",
      "recommendedActions": "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
      "entityMappings": {
        "accounts": [
          {
            "nameColumn": "AccountName",
            "ntDomainColumn": "AccountDomain",
            "sidColumn": "AccountSid"
          }
        ],
        "hosts": [
          {
            "deviceIdColumn": "DeviceId",
            "nameColumn": "DeviceName"
          }
        ],
        "files": [
          {
            "nameColumn": "FileName",
            "sha1Column": "SHA1",
            "sha256Column": "SHA256"
          }
        ]
      },
      "tactics": [
        {
          "tactic": "Execution",
          "techniques": [
            {
              "technique": "T1059.001"
            }
          ]
        }
      ]
    }
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/security/rules/detectionRules/office-encoded-powershell

{
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "office-encoded-powershell",
  "displayName": "Suspicious encoded PowerShell from Office",
  "description": "Detects encoded PowerShell processes launched by Office applications, a common phishing payload pattern.",
  "status": "enabled",
  "createdBy": "alice@contoso.com",
  "createdDateTime": "2026-05-25T10:15:00Z",
  "lastModifiedBy": "alice@contoso.com",
  "lastModifiedDateTime": "2026-05-25T10:15:00Z",
  "queryCondition": {
    "queryText": "DeviceProcessEvents | where InitiatingProcessFileName in~ ('winword.exe','excel.exe','outlook.exe') | where FileName == 'powershell.exe' | where ProcessCommandLine has '-enc'"
  },
  "schedule": {
    "frequency": "PT1H"
  },
  "detectionAction": {
    "alertTemplate": {
      "title": "Suspicious encoded PowerShell from Office",
      "description": "An Office app launched an encoded PowerShell command, which may indicate phishing-driven code execution.",
      "severity": "high",
      "recommendedActions": "Investigate the parent Office document, isolate the device, and review the user's recent email activity.",
      "entityMappings": {
        "accounts": [
          {
            "nameColumn": "AccountName",
            "sidColumn": "AccountSid"
          }
        ]
      },
      "tactics": [
        {
          "tactic": "Execution",
          "techniques": [
            {
              "technique": "T1059.001"
            }
          ]
        }
      ]
    },
    "automatedActions": {
      "isolateDevices": [
        {
          "deviceIdColumn": "DeviceId",
          "isolationType": "full"
        }
      ],
      "initiateInvestigations": [
        {
          "deviceIdColumn": "DeviceId"
        }
      ]
    }
  }
}
```
