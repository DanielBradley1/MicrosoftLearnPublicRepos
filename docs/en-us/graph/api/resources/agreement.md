<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-08 -->

# agreement resource type

Namespace: microsoft.graph

Represents a tenant's customizable terms of use agreement that is created and managed with Microsoft Entra ID Governance. You can use the following methods to create and manage the [Microsoft Entra Terms of Use feature](#related-content) according to your scenario.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/termsofusecontainer-list-agreements?view=graph-rest-1.0) | [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) collection | Get an agreement object collection. |
| [Create](https://learn.microsoft.com/en-us/graph/api/termsofusecontainer-post-agreements?view=graph-rest-1.0) | [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) | Create a new agreement by posting to the agreement collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agreement-get?view=graph-rest-1.0) | [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) | Read properties and relationships of an agreement object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agreement-update?view=graph-rest-1.0) | None | Update an agreement object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agreement-delete?view=graph-rest-1.0) | None | Delete an agreement object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the agreement. The display name is used for internal tracking of the agreement but isn't shown to end users who view the agreement. Supports `$filter` \(`eq`\). |
| id | String | The identifier of the agreement. Read-only. Supports `$filter` \(`eq`\). |
| isPerDeviceAcceptanceRequired | Boolean | Indicates whether end users are required to accept this agreement on every device that they access it from. The end user is required to register their device in Microsoft Entra ID, if they haven't already done so. Supports `$filter` \(`eq`\). |
| isViewingBeforeAcceptanceRequired | Boolean | Indicates whether the user has to expand the agreement before accepting. Supports `$filter` \(`eq`\). |
| termsExpiration | [termsExpiration](https://learn.microsoft.com/en-us/graph/api/resources/termsexpiration?view=graph-rest-1.0) | Expiration schedule and frequency of agreement for all users. Supports `$filter` \(`eq`\). |
| userReacceptRequiredFrequency | Duration | The duration after which the user must reaccept the terms of use. The value is represented in ISO 8601 format for durations. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| acceptances | [agreementAcceptance](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0) collection | Read-only. Information about acceptances of this agreement. |
| file | [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) | Default PDF linked to this agreement. |
| files | [agreementFileLocalization](https://learn.microsoft.com/en-us/graph/api/resources/agreementfilelocalization?view=graph-rest-1.0) collection | PDFs linked to this agreement. This property is in the process of being deprecated. Use the **file** property instead. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agreement",
  "displayName": "String",
  "id": "String (identifier)",
  "isPerDeviceAcceptanceRequired": "Boolean",
  "isViewingBeforeAcceptanceRequired": "Boolean",
  "termsExpiration": {
    "@odata.type": "microsoft.graph.termsExpiration"
  },
  "userReacceptRequiredFrequency": "String (duration)"
}
```

## Related content

- [Microsoft Entra Terms of Use](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/terms-of-use)
