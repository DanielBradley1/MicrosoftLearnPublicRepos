<!-- Source: https://learn.microsoft.com/en-us/graph/api/customfielddefinition-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update customFieldDefinition

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a customFieldDefinition object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}
PATCH /users/{usersId}/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| planId | String | ID of the plan the custom field is defined on. Required, and immutable after creation. Required. |
| displayName | String | Name of the custom field. Required. |
| valueType | customFieldValueType | Data type of the custom field's values.. The possible values are: `text`, `date`, `utcDateTime`, `number`, `decimal`, `flag`, `singleChoiceText`, `multipleChoiceText`, `unknownFutureValue`. Optional. |
| rollupType | customFieldRollupType | How values of this custom field are rolled up across tasks. The possible values are: `noRollup`, `max`, `min`, `sum`, `average`, `unknownFutureValue`. Optional. |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/me/planner/plans_v2/{planId}/customFieldDefinitions/{customFieldDefinitionId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customFieldDefinition",
  "planId": "b3d9f9a2-3e14-4a4b-9b2b-6b6d9e6a2f31",
  "displayName": "Budget",
  "valueType": "number",
  "rollupType": "sum",
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customFieldDefinition",
  "id": "590f4e29-112d-432c-491b-21a16ed31803",
  "planId": "String",
  "displayName": "String",
  "valueType": "String",
  "rollupType": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "deletedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "deletedDateTime": "String (timestamp)",
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  }
}
```
