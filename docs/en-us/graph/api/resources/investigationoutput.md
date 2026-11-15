<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/investigationoutput?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# investigationOutput resource type

Namespace: microsoft.graph

Represents a stored output file owned by an agentic session. Read its **id** and **kind** metadata, or use its **id** to download the stored file through the authenticated **content** route. Metadata and content requests enforce the parent session's authorization.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List outputs](https://learn.microsoft.com/en-us/graph/api/investigationsession-list-outputs?view=graph-rest-beta) | [investigationOutput](https://learn.microsoft.com/en-us/graph/api/resources/investigationoutput?view=graph-rest-beta) collection | Get the session outputs. |
| [Get](https://learn.microsoft.com/en-us/graph/api/investigationoutput-get?view=graph-rest-beta) | [investigationOutput](https://learn.microsoft.com/en-us/graph/api/resources/investigationoutput?view=graph-rest-beta) | Read output metadata. |
| [Get content](https://learn.microsoft.com/en-us/graph/api/investigationoutput-get-content?view=graph-rest-beta) | Stream | Download the authenticated output stream. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The output bytes, retrieved through `/security/agenticSecurity/sessions/{session-id}/outputs/{output-id}/content`. The stream isn't inline in the metadata response. Read-only. |
| id | String | The stable, opaque stored-file identifier, unique within its containing session. Read-only. |
| kind | investigationOutputType | The output category. The possible values are: `summary`, `artifact`, `unknownFutureValue`. Both summary text and artifact bytes are retrieved through the authenticated content route. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.investigationOutput",
  "id": "String (identifier)",
  "kind": "String",
  "content": "Stream"
}
```
