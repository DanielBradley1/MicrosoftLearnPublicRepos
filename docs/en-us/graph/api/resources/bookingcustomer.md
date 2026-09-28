<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingCustomer resource type

Namespace: microsoft.graph

Represents a customer of a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

Inherits from [bookingCustomerBase](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerbase?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-customers?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) collection | Get a list of **bookingCustomer** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) | Create a new **bookingCustomer** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingcustomer-get?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) | Read the properties and relationships of a **bookingCustomer** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingcustomer-update?view=graph-rest-1.0) | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) | Update a **bookingCustomer** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingcustomer-delete?view=graph-rest-1.0) | None | Delete a **bookingCustomer** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addresses | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) collection | Addresses associated with the customer. The attribute **type** of **physicalAddress** isn't supported in v1.0. Internally we map the addresses to the type `others`. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the customer was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The name of the customer. |
| emailAddress | String | The SMTP address of the customer. |
| id | String | The ID of the customer. Read-only. Inherited from [bookingCustomerBase](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerbase?view=graph-rest-1.0). |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the customer was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| phones | [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone?view=graph-rest-1.0) collection | Phone numbers associated with the customer, including home, business, and mobile numbers. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingCustomer",
  "addresses": [{"@odata.type": "microsoft.graph.physicalAddress"}],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "emailAddress": "String",
  "id": "String (identifier)",
  "lastUpdatedDateTime": "String (timestamp)",
  "phones": [{"@odata.type": "microsoft.graph.phone"}]
}
```
