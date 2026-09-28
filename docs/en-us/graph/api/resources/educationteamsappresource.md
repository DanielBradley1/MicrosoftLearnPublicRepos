<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationteamsappresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationTeamsAppResource resource type

Namespace: microsoft.graph

Corresponds to an [installed Microsoft Teams app](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0). This allows education service users to create and share assignments with embedded Teams applications, such as YouTube or Flip.

For information about using Flip for education on Microsoft Teams, see [introduction to Flip](https://learn.microsoft.com/en-us/training/educator-center/product-guides/flip).

Inherits from [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appIconWebUrl | String | URL that points to the icon of the app. |
| appId | String | Teams app ID of the application. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who created this resource. Inherited from **educationResource**. |
| createdDateTime | DateTimeOffset | The date and time when the resource was added. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from **educationResource**. |
| displayName | String | The display name of the resource. Inherited from **educationResource**. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who last modified the resource. Inherited from **educationResource**. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from **educationResource**. |
| teamsEmbeddedContentUrl | String | URL for the app resource that will be opened by Teams. |
| webUrl | String | URL for the app resource that can be opened in the browser. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appIconWebUrl": "String",
  "appId": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "teamsEmbeddedContentUrl": "String",
  "webUrl": "String"
}
```
