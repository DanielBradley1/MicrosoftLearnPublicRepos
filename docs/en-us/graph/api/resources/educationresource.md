<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationResource resource type

Namespace: microsoft.graph

An abstract type that represents the base class for all education-related resource objects in a system.

Base type of the following resources:

- [educationExcelResource](https://learn.microsoft.com/en-us/graph/api/resources/educationexcelresource?view=graph-rest-1.0)
- [educationExternalResource](https://learn.microsoft.com/en-us/graph/api/resources/educationexternalresource?view=graph-rest-1.0)
- [educationFileResource](https://learn.microsoft.com/en-us/graph/api/resources/educationfileresource?view=graph-rest-1.0)
- [educationLinkResource](https://learn.microsoft.com/en-us/graph/api/resources/educationlinkresource?view=graph-rest-1.0)
- [educationMediaResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmediaresource?view=graph-rest-1.0)
- [educationPowerPointResource](https://learn.microsoft.com/en-us/graph/api/resources/educationpowerpointresource?view=graph-rest-1.0)
- [educationSpeakerProgressResource](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource?view=graph-rest-1.0)
- [educationTeamsAppResource](https://learn.microsoft.com/en-us/graph/api/resources/educationteamsappresource?view=graph-rest-1.0)
- [educationWordResource](https://learn.microsoft.com/en-us/graph/api/resources/educationwordresource?view=graph-rest-1.0)

An educationResource is associated with an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) and/or [submission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0), which represents the learning object that is being handed out or handed in. You cannot instantiate a resource directly; you must make a subclass that will represent the type of resource being used.

This resource stores the common properties across all resource types.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The individual who created the resource. |
| createdDateTime | DateTimeOffset | Moment in time when the resource was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| displayName | String | Display name of resource. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. |
| lastModifiedDateTime | DateTimeOffset | Moment in time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
