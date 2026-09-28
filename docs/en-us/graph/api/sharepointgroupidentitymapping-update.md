<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointgroupidentitymapping-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update sharePointGroupIdentityMapping

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Perform delta patch operations on [group identity mappings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) for cross-organization migration. This operation supports bulk add, update, and delete actions for both Microsoft 365 groups and regular Microsoft Entra groups. Maximum of 50 items allowed in the value array.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SharePointCrossTenantMigration.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SharePointCrossTenantMigration.Manage.All | Not available. |

## HTTP request

```http
PATCH /solutions/sharePoint/migrations/crossOrganizationGroupMappings
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
| deleted | [deleted](https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-beta) | Indicates that an identity mapping was deleted successfully. Optional. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| groupType | sharePointIdentityMappingGroupType | Indicates the type of group. The possible values are: `none`, `regularGroup`, `m365Group`, `unknownFutureValue`. |
| sourceGroupIdentity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The identity information of the source group. |
| sourceOrganizationId | Guid | The unique identifier of the source organization in the migration. Inherited from [sharePointIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymapping?view=graph-rest-beta). |
| targetGroupIdentity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The identity information of the target group. |
| targetGroupMigrationData | [sharePointIdentityMappingGroupMigrationData](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentitymappinggroupmigrationdata?view=graph-rest-beta) | Additional migration-specific data for the target group. |

## Response

If successful, this method returns a `200 OK` response code and a collection of updated [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request that includes both updates and removals using the **@removed** annotation.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationGroupMappings
Content-Type: application/json

{
  "@context": "#$delta",
  "value": [
    {
      "sourceOrganizationId": "11111111-1111-1111-1111-111111111111",
      "groupType": "m365Group",
      "sourceGroupIdentity": {
        "id": "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
      },
      "targetGroupIdentity": {
        "id": "bbbbbbbb-bbbb-bbbb-bbbb-bbbbbbbbbbbb"
      },
      "targetGroupMigrationData": {
        "mailNickname": "targetGroup"
      }
    },
    {
      "@removed": {
        "reason": "deleted"
      },
      "sourceGroupIdentity": {
        "id": "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
      }
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossOrganizationGroupMappings = {
  '@context': '#$delta',
  value: [
    {
      sourceOrganizationId: '11111111-1111-1111-1111-111111111111',
      groupType: 'm365Group',
      sourceGroupIdentity: {
        id: 'aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa'
      },
      targetGroupIdentity: {
        id: 'bbbbbbbb-bbbb-bbbb-bbbb-bbbbbbbbbbbb'
      },
      targetGroupMigrationData: {
        mailNickname: 'targetGroup'
      }
    },
    {
      '@removed': {
        reason: 'deleted'
      },
      sourceGroupIdentity: {
        id: 'aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa'
      }
    }
  ]
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationGroupMappings')
	.version('beta')
	.update(crossOrganizationGroupMappings);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#solutions/sharePoint/migrations/crossOrganizationGroupMappings/$delta",
  "value": [
    {
      "id": "AQAAAAIAAABhYWFhYWFhYS1hYWFhLWFhYWEtYWFhYS1hYWFhYWFhYWFhYWE",
      "sourceOrganizationId": "11111111-1111-1111-1111-111111111111",
      "groupType": "m365Group",
      "sourceGroupIdentity": {
        "id": "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
      },
      "targetGroupIdentity": {
        "id": "bbbbbbbb-bbbb-bbbb-bbbb-bbbbbbbbbbbb"
      },
      "targetGroupMigrationData": {
        "mailNickname": "targetGroup"
      }
    },
    {
      "id": "AQAAAAIAAABhYWFhYWFhYS1hYWFhLWFhYWEtYWFhYS1hYWFhYWFhYWFhYWE",
      "sourceGroupIdentity": {
        "id": "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
      },
      "deleted": {
        "state": "deleted"
      }
    }
  ]
}
```
