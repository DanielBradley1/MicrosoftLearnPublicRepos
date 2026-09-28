<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# actionResultPart resource type

Namespace: microsoft.graph

An abstract type that serves as a base to model responses of bulk operations. The **error** property is selectively populated based on whether the response represents an error.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | The error that occurred, if any, during the bulk operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.actionResultPart",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```

## Related content

- [Add members in bulk to a team](https://learn.microsoft.com/en-us/graph/api/conversationmembers-add?view=graph-rest-1.0)
- [Remove members in bulk from a team](https://learn.microsoft.com/en-us/graph/api/conversationmember-remove?view=graph-rest-1.0)
