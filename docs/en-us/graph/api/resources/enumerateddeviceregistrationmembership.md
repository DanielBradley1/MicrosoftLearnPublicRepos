<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumerateddeviceregistrationmembership?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# enumeratedDeviceRegistrationMembership resource type

Namespace: microsoft.graph

Indicates that this device registration policy applies to the enumerated users and groups. Inherits from [deviceRegistrationMembership](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationmembership?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groups | String collection | List of groups that this policy applies to. |
| users | String collection | List of users that this policy applies to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedDeviceRegistrationMembership",
  "users": [
    "String"
  ],
  "groups": [
    "String"
  ]
}
```
