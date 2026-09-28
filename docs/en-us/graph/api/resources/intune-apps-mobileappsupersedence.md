<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppSupersedence resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Describes a supersedence relationship between two mobile apps.

Inherits from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppSupersedences](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappsupersedence-list?view=graph-rest-beta) | [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) objects. |
| [Get mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappsupersedence-get?view=graph-rest-beta) | [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) | Read properties and relationships of the [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) object. |
| [Create mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappsupersedence-create?view=graph-rest-beta) | [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) | Create a new [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) object. |
| [Delete mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappsupersedence-delete?view=graph-rest-beta) | None | Deletes a [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta). |
| [Update mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappsupersedence-update?view=graph-rest-beta) | [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) | Update the properties of a [mobileAppSupersedence](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedence?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the mobile app relationship entity. This unique identifier is assigned at MobileAppRelationship entity creation. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672\_43aaaf35-ce51-4695-9447-5eac6df31161. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetId | String | The unique app identifier of the target of the mobile app relationship entity. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetDisplayName | String | The display name of the app that is the target of the mobile app relationship entity. For example: Firefox Setup 52.0.2 32bit.intunewin. Maximum length is 500 characters. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetDisplayVersion | String | The display version of the app that is the target of the mobile app relationship entity. For example 1.0 or 1.2203.156. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetPublisher | String | The publisher of the app that is the target of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Returned by default. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetPublisherDisplayName | String | The publisher display name of the app that is the target of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceId | String | The unique app identifier of the source of the mobile app relationship entity. For example: 2dbc75b9-e993-4e4d-a071-91ac5a218672. If null during relationship creation, then it will be populated with parent Id. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceDisplayName | String | The display name of the app that is the source of the mobile app relationship entity. For example: Orca. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourceDisplayVersion | String | The display version of the app that is the source of the mobile app relationship entity. For example 1.0.12 or 1.2203.156 or 3. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| sourcePublisherDisplayName | String | The publisher display name of the app that is the source of the mobile app relationship entity. For example: Fabrikam. Maximum length is 500 characters. Read-Only. Supports: $select. Does not support $search, $filter, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) |
| targetType | [mobileAppRelationshipType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationshiptype?view=graph-rest-beta) | The type of relationship indicating whether the target application of a relationship is a parent or child in the relationship. Possible values are: parent, child. Read-Only. Returned by default. Supports: $select, $filter. Does not support $search, $orderBy. This property is read-only. Inherited from [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta). Possible values are: `child`, `parent`, `unknownFutureValue`. |
| supersedenceType | [mobileAppSupersedenceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappsupersedencetype?view=graph-rest-beta) | The supersedence relationship type between the parent and child apps. Possible values are: update, replace. Read-Only. Possible values are: `update`, `replace`, `unknownFutureValue`. |
| supersededAppCount | Int32 | The total number of apps directly or indirectly superseded by the child app. Read-Only. This property is read-only. |
| supersedingAppCount | Int32 | The total number of apps directly or indirectly superseding the parent app. Read-Only. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppSupersedence",
  "id": "String (identifier)",
  "targetId": "String",
  "targetDisplayName": "String",
  "targetDisplayVersion": "String",
  "targetPublisher": "String",
  "targetPublisherDisplayName": "String",
  "sourceId": "String",
  "sourceDisplayName": "String",
  "sourceDisplayVersion": "String",
  "sourcePublisherDisplayName": "String",
  "targetType": "String",
  "supersedenceType": "String",
  "supersededAppCount": 1024,
  "supersedingAppCount": 1024
}
```
