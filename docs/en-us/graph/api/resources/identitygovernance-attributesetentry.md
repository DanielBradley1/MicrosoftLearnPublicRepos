<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attributesetentry?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# attributeSetEntry resource type

Namespace: microsoft.graph.identityGovernance

Represents a key-value pair in an attribute set. This object is configured in the **attributeSetEntries** property of the [provisioningObjectWorkflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-provisioningobjectworkflowsubject?view=graph-rest-1.0) resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name \(key\) of the attribute. |
| value | String | The value of the attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.attributeSetEntry",
  "name": "String",
  "value": "String"
}
```
