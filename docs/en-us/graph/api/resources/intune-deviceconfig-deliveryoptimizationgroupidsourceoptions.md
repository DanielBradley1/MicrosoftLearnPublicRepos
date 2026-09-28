<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationgroupidsourceoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deliveryOptimizationGroupIdSourceOptions resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Group id options type

Inherits from [deliveryOptimizationGroupIdSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationgroupidsource?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupIdSourceOption | [deliveryOptimizationGroupIdOptionsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationgroupidoptionstype?view=graph-rest-beta) | Set this policy to restrict peer selection to a specific source. Possible values are: `notConfigured`, `adSite`, `authenticatedDomainSid`, `dhcpUserOption`, `dnsSuffix`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deliveryOptimizationGroupIdSourceOptions",
  "groupIdSourceOption": "String"
}
```
