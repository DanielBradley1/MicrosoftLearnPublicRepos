<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keyrealvaluepair?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# keyRealValuePair resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A key-value pair with a string key and a real \(floating-point\) value.

Inherits from [keyTypedValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keytypedvaluepair?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | The string key of the key-value pair. Inherited from [keyTypedValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keytypedvaluepair?view=graph-rest-beta) |
| value | Double | The real \(floating-point\) value of the key-value pair. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.keyRealValuePair",
  "key": "String",
  "value": "4.2"
}
```
