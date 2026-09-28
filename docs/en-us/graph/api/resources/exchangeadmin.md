<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangeadmin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# exchangeAdmin resource type

Namespace: microsoft.graph

Represents a container for the Exchange admin functionality.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| mailboxes | [mailbox](https://learn.microsoft.com/en-us/graph/api/resources/mailbox?view=graph-rest-1.0) collection | Represents a user's mailboxes. |
| tracing | [messageTracingRoot](https://learn.microsoft.com/en-us/graph/api/resources/messagetracingroot?view=graph-rest-1.0) | Represents a container for administrative resources to trace messages. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeAdmin"
}
```
