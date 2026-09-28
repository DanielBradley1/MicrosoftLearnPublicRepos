<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# impactedResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra resource in your tenant that's associated with a Microsoft Entra ID [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/recommendation-list-impactedresources?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) collection | Get the [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) resources from the impactedResources navigation property. |
| [Get](https://learn.microsoft.com/en-us/graph/api/impactedresource-get?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Read the properties and relationships of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object. |
| [Postpone](https://learn.microsoft.com/en-us/graph/api/impactedresource-postpone?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `postponed` to a specified date and time. |
| [Dismiss](https://learn.microsoft.com/en-us/graph/api/impactedresource-dismiss?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `dismissed`. |
| [Complete](https://learn.microsoft.com/en-us/graph/api/impactedresource-complete?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `completedByUser`. |
| [Reactivate](https://learn.microsoft.com/en-us/graph/api/impactedresource-reactivate?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `active`. |
| [Mark planned](https://learn.microsoft.com/en-us/graph/api/impactedresource-markplanned?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `planned`. |
| [Accept risk](https://learn.microsoft.com/en-us/graph/api/impactedresource-acceptrisk?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `riskAccepted`. |
| [Apply alternate mitigation](https://learn.microsoft.com/en-us/graph/api/impactedresource-applyalternatemitigation?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Mark the status of an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object as `alternateMitigation`. |
| [Add tag](https://learn.microsoft.com/en-us/graph/api/impactedresource-addtag?view=graph-rest-beta) | [recommendationTag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) | Add a user-defined tag to an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta). |
| [Remove tag](https://learn.microsoft.com/en-us/graph/api/impactedresource-removetag?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) | Remove a user-defined tag from an [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta). |
| [Add tag to multiple resources](https://learn.microsoft.com/en-us/graph/api/impactedresource-addtag-collection?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) collection | Add the same tag to up to 50 [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) objects in a single request. |
| [Remove tag from multiple resources](https://learn.microsoft.com/en-us/graph/api/impactedresource-removetag-collection?view=graph-rest-beta) | [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) collection | Remove the same tag from up to 50 [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) objects in a single request. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedDateTime | DateTimeOffset | The date and time when the [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) object was initially associated with the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). |
| additionalDetails | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-beta) collection | Additional information unique to the [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) to help contextualize the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta). |
| apiUrl | String | The URL link to the corresponding Microsoft Entra resource. |
| displayName | String | Friendly name of the Microsoft Entra resource. |
| id | String | A unique identifier of the impacted Microsoft Entra resource. |
| lastModifiedBy | String | Name of the user or service that last updated the **status**. |
| lastModifiedDateTime | String | The date and time when the **status** was last updated. |
| owner | String | The user responsible for maintaining the resource. |
| portalUrl | String | The URL link to the corresponding Microsoft Entra admin center page of the resource. |
| postponeUntilDateTime | DateTimeOffset | The future date and time when the **status** of a postponed [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta) will be `active` again. |
| rank | Int32 | Indicates the importance of the resource. A resource with a rank equal to 1 is of the highest importance. |
| recommendationId | String | The unique identifier of the [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) that the resource is associated with. |
| resourceType | String | Indicates the type of Microsoft Entra resource. Examples include `user`, `application`. |
| status | recommendationStatus | Indicates whether a resource needs to be addressed. The possible values are: `active`, `completedBySystem`, `completedByUser`, `dismissed`, `postponed`, `unknownFutureValue`, `riskAccepted`, `thirdParty`, `planned`, `alternateMitigation`, `needsMoreAction`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `riskAccepted` , `thirdParty` , `planned` , `alternateMitigation` , `needsMoreAction`. By default, a recommendation's **status** is set to `active` when the recommendation is first generated. **Status** is set to `completedBySystem` when our service detects that a resource which was once active no longer applies. |
| subjectId | String | The related unique identifier, depending on the **resourceType**. For example, this property is set to the `applicationId` if the **resourceType** is an `application`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tags | [recommendationTag](https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta) collection | The user-defined free-form labels applied to the [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta). The collection isn't directly writable; tags are created and removed through the [addTag](https://learn.microsoft.com/en-us/graph/api/impactedresource-addtag?view=graph-rest-beta) and [removeTag](https://learn.microsoft.com/en-us/graph/api/impactedresource-removetag?view=graph-rest-beta) actions. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.impactedResource",
  "id": "String (identifier)",
  "subjectId": "String",
  "recommendationId": "String",
  "addedDateTime": "String (timestamp)",
  "portalUrl": "String",
  "apiUrl": "String",
  "displayName": "String",
  "resourceType": "String",
  "owner": "String",
  "rank": "Integer",
  "status": "String",
  "additionalDetails": [
    {
      "@odata.type": "microsoft.graph.keyValue"
    }
  ],
  "lastModifiedBy": "String",
  "lastModifiedDateTime": "String",
  "postponeUntilDateTime": "String (timestamp)"
}
```
