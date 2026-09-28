<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Update assignment

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object to enable or disable services. Any service contained in its allotment which isn't listed in the **disabledServicePlanIds** array is enabled.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions to update an **assignment** for an admin:

```http
PATCH /admin/cloudLicensing/assignments/{assignmentId}
PATCH /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
```

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing.AssignLicenses | CloudLicensing.AssignLicenses.Organization, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing.AssignLicenses.Organization | Directory.ReadWrite.All |

Permissions to update an **assignment** for a user:

```http
PATCH /me/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
PATCH /users/{userId}/cloudLicensing/assignments/{assignmentId}
```

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-CloudLicensing.AssignLicenses | User-CloudLicensing.AssignLicenses.Organization, AgentIdUser.ReadWrite.IdentityParentedBy, AgentIdUser.ReadWrite.All, User.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-CloudLicensing.AssignLicenses.Organization | AgentIdUser.ReadWrite.IdentityParentedBy, AgentIdUser.ReadWrite.All, User.ReadWrite.All, Directory.ReadWrite.All |

Permissions to update an **assignment** for a group:

```http
PATCH /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
```

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-CloudLicensing.AssignLicenses | Group-CloudLicensing.AssignLicenses.Organization, Group.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-CloudLicensing.AssignLicenses.Organization | Group.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

To update an assignment for the signed-in user using delegated \(`/me`\) permissions:

```http
PATCH /me/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
```

To update an assignment using either delegated or application permissions:

```http
PATCH /admin/cloudLicensing/assignments/{assignmentId}
PATCH /admin/cloudLicensing/allotments/{allotmentId}/assignments/{assignmentId}
PATCH /groups/{groupId}/cloudLicensing/assignments/{assignmentId}
PATCH /users/{userId}/cloudLicensing/assignments/{assignmentId}
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
| disabledServicePlanIds | GUID collection | The list of disabled service plans for this assignment. An empty list indicates that all services are enabled. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/me/cloudLicensing/assignments/0b1a424d-3b9b-4446-80b9-6917dd521e03
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ],
  "allotment@odata.bind": "https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi",
  "assignedTo@odata.bind": "https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const assignment = {
  '@odata.type': '#microsoft.graph.cloudLicensing.assignment',
  disabledServicePlanIds: [
    'bed136c6-b799-4462-824d-fc045d3a9d25'
  ],
  'allotment@odata.bind': 'https://graph.microsoft.com/beta/admin/cloudLicensing/allotments/rkocgef3dgjhnu3gmu2mqhbdbmwcymnf6fk3k6a7zbui5e7gfpmi',
  'assignedTo@odata.bind': 'https://graph.microsoft.com/beta/users/6d645c5f-089f-40d8-b0e7-136fb5c56d5b'
};

await client.api('/me/cloudLicensing/assignments/0b1a424d-3b9b-4446-80b9-6917dd521e03')
	.version('beta')
	.update(assignment);
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
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": [
    "bed136c6-b799-4462-824d-fc045d3a9d25"
  ],
  "id": "405ee855-dd74-f695-8d7e-be35a6788fe8"
}
```
