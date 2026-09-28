<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# insiderRiskyUserApproval resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the approval configuration for risky users detected by Microsoft Purview Insider Risk Management.

Inherits from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/insiderriskyuserapproval-get?view=graph-rest-beta) | [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) | Read the properties and relationships of [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/insiderriskyuserapproval-update?view=graph-rest-beta) | [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) | Update the properties of an [insiderRiskyUserApproval](https://learn.microsoft.com/en-us/graph/api/resources/insiderriskyuserapproval?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The userPrincipalName of the user or identity of the subject who created this resource. Read-only. Inherited from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta). |
| id | String | The unique identifier for an entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isApprovalRequired | Boolean | Indicates whether approval is required for risky users. |
| isEnabled | Boolean | Indicates whether the control configuration is enabled. Inherited from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta). |
| minimumRiskLevel | purviewInsiderRiskManagementLevel | The minimum risk level for which approval is required. The possible values are: `none`, `minor`, `moderate`, `elevated`, `unknownFutureValue`. |
| modifiedBy | String | The userPrincipalName of the user who last modified this resource. Read-only. Inherited from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.insiderRiskyUserApproval",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedBy": "String",
  "modifiedDateTime": "String (timestamp)",
  "isApprovalRequired": "Boolean",
  "minimumRiskLevel": "String"
}
```
