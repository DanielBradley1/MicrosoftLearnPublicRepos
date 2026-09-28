<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeylongvaluepair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# stringKeyLongValuePair resource type

Namespace: microsoft.graph

Represents a key-value pair where the key is a string and the value is an Int64. This object is configured in the **synchronizedEntryCountByType** property of [synchronizationStatus](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationstatus?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | The mapping of the user type from the source system to the target system. For example:  <br><br><br><li><code>User to User</code> - For Microsoft Entra ID to Microsoft Entra ID synchronization <br></li><br><br><li><code>worker to user</code> - For Workday to Microsoft Entra synchronization. <br></li> |
| value | Int64 | Total number of synchronized objects. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "key": "String",
  "value": "Integer"
}
```
