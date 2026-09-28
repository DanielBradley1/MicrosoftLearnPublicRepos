<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingperson?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# bookingPerson resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This resource type is a base type for a person in a Microsoft Bookings business, which can be a [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-beta) or [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-beta).

Inherits from [bookingNamedEntity](https://learn.microsoft.com/en-us/graph/api/resources/bookingnamedentity?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | A name for the derived entity, which interfaces with customers. Inherited from **bookingNamedEntity**. |
| emailAddress | String | The email address of the person. |
| id | String | The ID for the derived entity. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "emailAddress": "String",
  "id": "String (identifier)"
}
```
