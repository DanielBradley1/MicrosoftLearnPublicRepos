<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-osversionapplicabilityrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# osVersionApplicabilityRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Inherits from [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filterType | [filterAssociationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-filterassociationtype?view=graph-rest-beta) | Inherited from [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta). Possible values are: `unknown`, `include`, `exclude`. |
| minOSVersion | String |  |
| maxOSVersion | String |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.osVersionApplicabilityRule",
  "filterType": "String",
  "minOSVersion": "String",
  "maxOSVersion": "String"
}
```
