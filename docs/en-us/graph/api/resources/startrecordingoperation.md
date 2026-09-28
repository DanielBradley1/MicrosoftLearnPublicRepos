<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/startrecordingoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# startRecordingOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the response format of a call start recording operation.

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
  "@odata.type": "#microsoft.graph.startRecordingOperation",
  "clientContext": "String (identifier)",
  "status": "NotStarted | Running | Completed | Failed"
}
```
