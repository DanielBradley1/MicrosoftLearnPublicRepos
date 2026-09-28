<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-companies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# company resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a company resource type in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get companies](https://learn.microsoft.com/en-us/graph/api/dynamics-companies-get?view=graph-rest-beta) | company | Get a company. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the company. Read-Only. |
| name | string | Specifies the Company. |
| displayName | string | Specifies the company display name. |
| systemVersion | string | Specifies the internal version of the company. |
| businessProfileId | string | Specifies the Business Profile ID linked to the company. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the company.

```json
{
  "id": "GUID",
  "name": "string",
  "displayName": "string",
  "systemVersion": "string",
  "businessProfileId": "string"
}
```
