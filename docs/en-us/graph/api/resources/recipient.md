<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# recipient resource type

Namespace: microsoft.graph

Represents information about a user in the sending or receiving end of an event, message or group post.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailAddress | [EmailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The recipient's email address. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "emailAddress": {"@odata.type": "microsoft.graph.emailAddress"}
}
```
