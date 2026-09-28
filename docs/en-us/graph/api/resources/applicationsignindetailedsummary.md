<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationsignindetailedsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# applicationSignInDetailedSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a detailed summary of an application sign-in.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-applicationsignindetailedsummary?view=graph-rest-beta) | [applicationSignInDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsignindetailedsummary?view=graph-rest-beta) collection | Retrieve **applicationSignInDetailedSummary** objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/applicationsignindetailedsummary-get?view=graph-rest-beta) | [applicationSignInDetailedSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsignindetailedsummary?view=graph-rest-beta) | Read the properties and relationships of an **applicationSignInDetailedSummary** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregatedEventDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| appDisplayName | String | Name of the application that the user signed in to. |
| appId | String | ID of the application that the user signed in to. |
| id | String | A unique ID representing the sign-in activity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| signInCount | Int64 | Count of sign-ins made by the application. |
| status | [signInStatus](https://learn.microsoft.com/en-us/graph/api/resources/signinstatus?view=graph-rest-beta) | Details of the sign-in status. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "aggregatedEventDateTime": "String (timestamp)",
  "appDisplayName": "String",
  "appId": "String",
  "id": "String (identifier)",
  "signInCount": "Int64",
  "status": {"@odata.type": "microsoft.graph.signInStatus"}
}
```
