<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# securityBaselineStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The security baseline compliance state summary for the security baseline of the account.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinestatesummary-get?view=graph-rest-beta) | [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) | Read properties and relationships of the [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) object. |
| [Update securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinestatesummary-update?view=graph-rest-beta) | [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) | Update the properties of a [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| secureCount | Int32 | Number of secure devices |
| notSecureCount | Int32 | Number of not secure devices |
| unknownCount | Int32 | Number of unknown devices |
| errorCount | Int32 | Number of error devices |
| conflictCount | Int32 | Number of conflict devices |
| notApplicableCount | Int32 | Number of not applicable devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityBaselineStateSummary",
  "id": "String (identifier)",
  "secureCount": 1024,
  "notSecureCount": 1024,
  "unknownCount": 1024,
  "errorCount": 1024,
  "conflictCount": 1024,
  "notApplicableCount": 1024
}
```
