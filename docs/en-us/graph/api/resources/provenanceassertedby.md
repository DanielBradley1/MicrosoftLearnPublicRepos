<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provenanceassertedby?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# provenanceAssertedBy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the actor that established an authentication method's [credentialProvenance](https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actorId | String | The identifier of the actor that established the provenance. |
| actorType | [provenanceActorType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#provenanceactortype-values) | The type of actor that established the provenance. The possible values are: `system`, `user`, `application`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.provenanceAssertedBy",
  "actorId": "String",
  "actorType": "String"
}
```
