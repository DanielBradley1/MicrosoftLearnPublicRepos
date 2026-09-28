<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingnamedentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# bookingNamedEntity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A base type for Microsoft Bookings entities that provide a display name, for example, [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-beta), [bookingPerson](https://learn.microsoft.com/en-us/graph/api/resources/bookingperson?view=graph-rest-beta), [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-beta), [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | A name for the derived entity, which interfaces with customers. |
| id | String | The ID for the derived entity. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)"
}
```
