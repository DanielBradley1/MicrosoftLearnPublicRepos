<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userregistrationactivitysummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# userRegistrationActivitySummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the summary of the number of successful/unsuccessful registration and reset events for each authentication method.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationmethodsroot-userregistrationactivity?view=graph-rest-beta) | [userRegistrationActivitySummary](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationactivitysummary?view=graph-rest-beta) collection | Get the summary of the number of successful/unsuccessful registration and reset events for each authentication method. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authMethod | [usageAuthMethod](https://learn.microsoft.com/en-us/graph/api/resources/usageauthmethod?view=graph-rest-beta) | The authentication method for the given summary. Supports `$filter` \(`eq`\). |
| failureActivityCount | Int64 | The total number of failed activities for the corresponding authMethod and feature. Supports `$filter` \(`eq`\). |
| feature | featureType | The type of activity. The possible values are: `registration`, `reset`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| id | String | The unique id for the given summary. Supports `$filter` \(`eq`\). |
| successfulActivityCount | Int64 | The total number of successful activities for the corresponding authMethod and feature. Supports `$filter` \(`gt`, `lt`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userRegistrationActivitySummary",
  "id": "String (identifier)",
  "feature": "String",
  "successfulActivityCount": "Integer",
  "failureActivityCount": "Integer",
  "authMethod": "String"
}
```
