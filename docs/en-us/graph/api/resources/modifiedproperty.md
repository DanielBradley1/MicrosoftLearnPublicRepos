<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/modifiedproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# modifiedProperty resource type

Namespace: microsoft.graph

Indicates all the properties on a Microsoft Entra resource that have been modified, including the old and new values. This object is configured in the **modifiedProperties** property of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0) and [targetResource](https://learn.microsoft.com/en-us/graph/api/resources/targetresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Indicates the property name of the target attribute that was changed. |
| newValue | String | Indicates the updated value for the propery. |
| oldValue | String | Indicates the previous value \(before the update\) for the property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "newValue": "String",
  "oldValue": "String"
}
```
