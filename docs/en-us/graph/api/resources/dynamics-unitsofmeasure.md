<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-unitsofmeasure?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# unitOfMeasure resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a unit of measure, which is a standard of measurement of a quantity, in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get units of measure](https://learn.microsoft.com/en-us/graph/api/dynamics-unitsofmeasure-get?view=graph-rest-beta) | unitOfMeasure | Get a unit of measure object. |
| [Create units of measure](https://learn.microsoft.com/en-us/graph/api/dynamics-create-unitsofmeasure?view=graph-rest-beta) | unitOfMeasure | Create a unit of measure object. |
| [Update units of measure](https://learn.microsoft.com/en-us/graph/api/dynamics-unitsofmeasure-update?view=graph-rest-beta) | unitOfMeasure | Update a unit of measure object. |
| [Delete units of measure](https://learn.microsoft.com/en-us/graph/api/dynamics-unitsofmeasure-delete?view=graph-rest-beta) | none | Delete a unit of measure object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the unitOfMeasure. Noneditable. |
| code | string | Specifies the code for the unit of measure. |
| displayName | string | Specifies the unit of measure's display name. |
| internationalStandardCode | string | Specifies the unit of measure code expressed according to the UNECE Rec20 standard for electronically ending sales documents. |
| lastModifiedDateTime | datetime | The last datetime the unit of measure was modified. Read-Only. |

## Relationships

None

## JSON representation

Here's a JSON representation of the **unitOfMeasure** resource.

```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "internationalStandardCode": "string",
  "lastModifiedDateTime": "datetime"
}
```
