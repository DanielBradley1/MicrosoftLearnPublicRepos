<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# processContentResponse resource type

Namespace: microsoft.graph

Contains the outcome of a processContent action or a single result within a processContentAsync action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| policyActions | Collection\([microsoft.graph.dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0)\) | A collection of policy actions \(like DLP actions\) triggered by the processed content. **NOTE**: Currently, the only policy action supported in for this resource type is `restrictAccess`. |
| processingErrors | Collection\([microsoft.graph.processingError](https://learn.microsoft.com/en-us/graph/api/resources/processingerror?view=graph-rest-1.0)\) | A collection of errors encountered during the content processing. |
| protectionScopeState | microsoft.graph.security.protectionScopeState | Indicates if the applicable protection scope \(policies\) has changed since the last known state for the context. Possible values are `modified` and `notModified`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processContentResponse",
  "policyActions": [
    {
      "@odata.type": "microsoft.graph.dlpActionInfo"
    }
  ],
  "processingErrors": [
    {
      "@odata.type": "microsoft.graph.processingError"
    }
  ],
  "protectionScopeState": "String"
}
```
