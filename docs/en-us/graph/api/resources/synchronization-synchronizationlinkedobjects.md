<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationlinkedobjects?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# synchronizationLinkedObjects resource type

Namespace: microsoft.graph

Represents any references to be provisioned during on-demand provisioning.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| members | [synchronizationJobSubject](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobsubject?view=graph-rest-1.0) collection | All group members that you would like to provision. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationLinkedObjects",
  "members": [
    {
      "@odata.type": "microsoft.graph.synchronizationJobSubject"
    }
  ]
}
```
