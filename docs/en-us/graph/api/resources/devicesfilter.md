<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicesfilter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-21 -->

# devicesFilter resource type

Namespace: microsoft.graph

Defines a rule to filter the devices and whether devices that satisfy the rule should be allowed or blocked.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mode | crossTenantAccessPolicyTargetConfigurationAccessType | Determines whether devices that satisfy the rule should be allowed or blocked. The possible values are: `allowed`, `blocked`, `unknownFutureValue`. |
| rule | String | Defines the rule to filter the devices. For example, `device.deviceAttribute2 -eq 'PrivilegedAccessWorkstation'`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.devicesFilter",
  "mode": "String",
  "rule": "String"
}
```
