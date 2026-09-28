<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-unclassifiedartifact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# unclassifiedArtifact resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents artifacts observed by Microsoft Security services that don't have a supporting API. While the threat intelligence APIs provide API support for many types of [artifacts](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0), some data elements either aren't yet supported or can't be supported. The **unclassifiedArtifact** resource extends artifacts, communicating what information has been gathered to allow for information analysis. An API isn't currently available to provide for further details.

This resource isn't an addressable. The data contained is meant to communicate available information where applicable.

Inherits from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The system-generated ID for this **unclassifiedArtifact**. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| kind | String | The kind for this **unclassifiedArtifact** resource, describing what this value means. |
| value | String | The value for this **unclassifiedArtifact**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.unclassifiedArtifact",
  "id": "String (identifier)",
  "kind": "String",
  "value": "String"
}
```
