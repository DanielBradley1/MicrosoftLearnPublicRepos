<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceConfigurationUserStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationuserstatesummary-get?view=graph-rest-beta) | [deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary?view=graph-rest-beta) | Read properties and relationships of the [deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary?view=graph-rest-beta) object. |
| [Update deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationuserstatesummary-update?view=graph-rest-beta) | [deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary?view=graph-rest-beta) | Update the properties of a [deviceConfigurationUserStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| unknownUserCount | Int32 | Number of unknown users |
| notApplicableUserCount | Int32 | Number of not applicable users |
| compliantUserCount | Int32 | Number of compliant users |
| remediatedUserCount | Int32 | Number of remediated users |
| nonCompliantUserCount | Int32 | Number of NonCompliant users |
| errorUserCount | Int32 | Number of error users |
| conflictUserCount | Int32 | Number of conflict users |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceConfigurationUserStateSummary",
  "id": "String (identifier)",
  "unknownUserCount": 1024,
  "notApplicableUserCount": 1024,
  "compliantUserCount": 1024,
  "remediatedUserCount": 1024,
  "nonCompliantUserCount": 1024,
  "errorUserCount": 1024,
  "conflictUserCount": 1024
}
```
