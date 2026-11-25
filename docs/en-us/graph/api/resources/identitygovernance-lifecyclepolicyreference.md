<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyReference resource type

Namespace: microsoft.graph.identityGovernance

Provides a lightweight reference to a lifecycle policy version. Returned in the **effectivePolicy** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the referenced lifecycle policy. |
| version | Int32 | The version of the referenced lifecycle policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyReference",
  "id": "String",
  "version": "Int32"
}
```
