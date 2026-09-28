<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# resultInfo resource type

Namespace: microsoft.graph

Provides success and failure-specific result information.

The code specifies if the result is a generic success or failure. If the code is 2xx, it's a success; if it's 4xx, it's a client error; and if it's 5xx, it's a server error.

The subcodes provide supplementary information related to the type of success or failure \(for example, a call transfer was successful\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | Int32 | The result code. |
| message | String | The message. |
| subcode | Int32 | The result subcode. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": 0,
  "message": "String",
  "subcode": 0
}
```
