<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/starttranscriptionoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-17 -->

# startTranscriptionOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the response format of a call start transcription operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique client context string. It can have a maximum of 256 characters. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.startTranscriptionOperation",
  "clientContext": "String (identifier)",
  "status": "NotStarted | Running | Completed | Failed"
}
```
