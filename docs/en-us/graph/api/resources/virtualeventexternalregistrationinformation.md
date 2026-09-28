<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalregistrationinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-09 -->

# virtualEventExternalRegistrationInformation resource type

Namespace: microsoft.graph

Represents the external information for a [virtual event registration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| referrer | String | A URL or string that represents the location from which the registrant registered. Optional. |
| registrationId | String | The identifier for a **virtualEventExternalRegistrationInformation** object. Optional. If set, the maximum supported length is 256 characters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventExternalRegistrationInformation",
  "referrer": "String",
  "registrationId": "String"
}
```
