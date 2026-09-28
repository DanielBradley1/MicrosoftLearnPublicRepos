<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationsigninsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# applicationSignInSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an application sign-in summary.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/reportroot-getazureadapplicationsigninsummary?view=graph-rest-beta) | [applicationSignInSummary](https://learn.microsoft.com/en-us/graph/api/resources/applicationsigninsummary?view=graph-rest-beta) | Read the properties and relationships of an **applicationSignInSummary** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appDisplayName | String | Name of the application that the user signed into. |
| failedSignInCount | Int64 | Count of failed sign-ins made by the application. |
| successPercentage | Int32 | Percentage of successful sign-ins made by the application. |
| successfulSignInCount | Int64 | Count of successful sign-ins made by the application. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appDisplayName": "String",
  "failedSignInCount": 1024,
  "successPercentage": 1024,
  "successfulSignInCount": 1024
}
```
