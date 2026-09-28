<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/positiondetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# positionDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about positions related to entities within a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| company | [companyDetail](https://learn.microsoft.com/en-us/graph/api/resources/companydetail?view=graph-rest-beta) | Information about the company or employer. |
| description | String | A description for the position in question. |
| employeeId | String | The identifier assigned to the employee. |
| employeeType | String | The type of employment for the position. |
| endMonthYear | Date | The date when the position ended. |
| jobTitle | String | The title of the position. |
| layer | Int32 | The place where the employee is within the organizational hierarchy. |
| level | String | The employee’s experience or management level. |
| role | String | The role the position entailed. |
| secondaryJobTitle | String | An optional job title for the position. |
| secondaryRole | String | An optional role for the position entailed. |
| startMonthYear | Date | The start date of the position. |
| summary | String | The summary of the position. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "company": {"@odata.type": "microsoft.graph.companyDetail"},
  "description": "String",
  "employeeId": "String",
  "employeeType": "String",
  "endMonthYear": "String (timestamp)",
  "jobTitle": "String",
  "layer": "Int32",
  "level": "String",
  "role": "String",
  "secondaryJobTitle": "String",
  "secondaryRole": "String",
  "startMonthYear": "String (timestamp)",
  "summary": "String"
}
```
