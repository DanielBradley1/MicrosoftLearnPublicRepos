<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobapplicationparameters?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# synchronizationJobApplicationParameters resource type

Namespace: microsoft.graph

Represents the objects that will be provisioned and the synchronization rules executed. The resource is primarily used for on-demand provisioning.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleId | String | The identifier of the [synchronizationRule](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-1.0) to be applied. This rule ID is defined in the [schema for a given synchronization job or template](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-get?view=graph-rest-1.0). |
| subjects | [synchronizationJobSubject](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobsubject?view=graph-rest-1.0) collection | The identifiers of one or more objects to which a synchronizationJob is to be applied. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationJobApplicationParameters",
  "ruleId": "String",
  "subjects": [
    {
      "@odata.type": "microsoft.graph.synchronizationJobSubject"
    }
  ]
}
```
