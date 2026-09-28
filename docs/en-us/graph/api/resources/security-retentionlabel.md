<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# retentionLabel resource type

Namespace: microsoft.graph.security

Represents how organizations, for compliance and governance purposes, can manage their data at an item level \(email or document\), including whether and for how long to retain or delete the item.

Organizations can use retention labels for different types of content that require different retention settings. For example, they can apply a retention label to tax forms and supporting documents to retain them for the period required by law.

Organizations can configure retention labels with the retention periods and actions based on factors such as the date last modified or created. They can also start different retention periods by specifying an [event that can trigger retention](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) when the event occurs.

For more information on how retention labels work, when to use them, and how Microsoft Purview supports retention labels to let you configure retention and deletion settings, see [Learn about retention policies and retention labels](https://learn.microsoft.com/en-us/purview/retention).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List retentionLabels](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-retentionlabel?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) collection | Get a list of the [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) objects and their properties. |
| [Create retentionLabel](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-retentionlabel?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Create a new [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [Get retentionLabel](https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-get?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Read the properties and relationships of a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [Update retentionLabel](https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-update?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Update the properties of a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [Delete retentionLabel](https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-delete?view=graph-rest-1.0) | None | Delete a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [List retentionEventType](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-list?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) collection | Get the retentionEventType resources from the exapnd eventType navigation property. |
| [Add retentionEventType](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-post?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Add eventType by adding the relevant odata property when creating a label. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionAfterRetentionPeriod | microsoft.graph.security.actionAfterRetentionPeriod | Specifies the action to take on the labeled document after the period specified by the retentionDuration property expires. The possible values are: `none`, `delete`, `startDispositionReview`, `unknownFutureValue`. |
| behaviorDuringRetentionPeriod | microsoft.graph.security.behaviorDuringRetentionPeriod | Specifies how the behavior of a document with this label should be during the retention period. The possible values are: `doNotRetain`, `retain`, `retainAsRecord`, `retainAsRegulatoryRecord`, `unknownFutureValue`. |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the retentionLabel. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the retentionLabel is created. |
| descriptionForAdmins | String | Provides label information for the admin. Optional. |
| descriptionForUsers | String | Provides the label information for the user. Optional. |
| displayName | String | Unique string that defines a label name. |
| id | String | Unique ID of the retentionLabel. |
| isInUse | Boolean | Specifies whether the label is currently being used. |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who last modified the retentionLabel. |
| lastModifiedDateTime | DateTimeOffset | The latest date time when the retentionLabel was modified. |
| retentionDuration | [microsoft.graph.security.retentionDuration](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionduration?view=graph-rest-1.0) | Specifies the number of days to retain the content. |
| retentionTrigger | microsoft.graph.security.retentionTrigger | Specifies whether the retention duration is calculated from the content creation date, labeled date, or last modification date. The possible values are: `dateLabeled`, `dateCreated`, `dateModified`, `dateOfEvent`, `unknownFutureValue`. |
| defaultRecordBehavior | microsoft.graph.security.defaultRecordBehavior | Specifies the locked or unlocked state of a record label when it is created.The possible values are: `startLocked`, `startUnlocked`, `unknownFutureValue`. |
| labelToBeApplied | String | Specifies the replacement label to be applied automatically after the retention period of the current label ends. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dispositionReviewStages | [microsoft.graph.security.dispositionReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0) collection | When action at the end of retention is chosen as 'dispositionReview', dispositionReviewStages specifies a sequential set of stages with at least one reviewer in each stage. |
| retentionEventType | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Represents the type associated with a retention event. |
| descriptors | [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0) | Represents out-of-the-box values that provide more options to improve the manageability and organization of the content you need to label. |

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.retentionLabel",
  "id": "String (identifier)",
  "displayName": "String",
  "behaviorDuringRetentionPeriod": "String",
  "actionAfterRetentionPeriod": "String",
  "retentionTrigger": "String",
  "retentionDuration": {
    "@odata.type": "microsoft.graph.security.retentionDuration"
  },
  "isInUse": "Boolean",
  "descriptionForAdmins": "String",
  "descriptionForUsers": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "labelToBeApplied": "String",
  "defaultRecordBehavior": "String"
}
```
