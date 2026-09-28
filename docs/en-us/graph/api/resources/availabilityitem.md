<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/availabilityitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# availabilityItem resource type

Namespace: microsoft.graph

Indicates the status of a [staff member](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) for a given time slot.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | dateTimeTimeZone | The end time of the time slot. |
| serviceId | String | Indicates the service ID for 1:n appointments. If the appointment is of type 1:n, this field is present, otherwise, `null`. |
| status | bookingsAvailabilityStatus | The status of the staff member. The possible values are: `available`, `busy`, `slotsAvailable`, `outOfOffice`, `unknownFutureValue`. |
| startDateTime | dateTimeTimeZone | The start time of the time slot. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "endDateTime": "DateTimeInfo",
  "serviceId": "String",
  "startDateTime": "DateTimeInfo",
  "status": "String"
}
```
