<!-- Source: https://learn.microsoft.com/en-us/graph/api/customdataprovidedresourceuploadsession-uploadfile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# customDataProvidedResourceUploadSession: uploadFile

Namespace: microsoft.graph

Upload a file in a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) created for an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}/uploadFile
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | multipart/form-data; boundary={your-boundary}. Required. |

## Request body

The body can contain a multipart message as shown in the example. The columns in the CSV should match the following required properties: `principalId`, `principalType`, `permissionId`, `permissionName`, `permissionDescription`, `permissionType`.

## Response

If successful, this action returns a `200 OK` response code and a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}/uploadFile
Content-Type: multipart/form-data; boundary=MyPartBoundary198374

--MyPartBoundary198374
Content-Disposition: form-data; name="file"; filename="building-access-data.csv"
Content-Type: application/octet-stream

principalId,principalType,permissionId,permissionName,permissionDescription,permissionType
550e8400-e29b-41d4-a716-446655440000,user,6ba7b810-9dad-11d1-80b4-00c04fd430c8,Access,Physical access to building,Physical
7c9e6679-7425-40de-944b-e07fc1f90ae7,user,6ba7b810-9dad-11d1-80b4-00c04fd430c9,Reserve,Book conference room,Administrative
--MyPartBoundary198374--
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customDataProvidedResourceUploadSession = --MyPartBoundary198374
Content-Disposition: form-data; name='file'; filename='building-access-data.csv'
Content-Type: application/octet-stream

principalId,principalType,permissionId,permissionName,permissionDescription,permissionType
550e8400-e29b-41d4-a716-446655440000,user,6ba7b810-9dad-11d1-80b4-00c04fd430c8,Access,Physical access to building,Physical
7c9e6679-7425-40de-944b-e07fc1f90ae7,user,6ba7b810-9dad-11d1-80b4-00c04fd430c9,Reserve,Book conference room,Administrative
--MyPartBoundary198374--;

await client.api('/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}/uploadFile')
	.post(customDataProvidedResourceUploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "@odata.type": "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "id": "0b64df22-1a83-472c-9556-6c3dc41742b9",
  "referenceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8",
  "status": "active",
  "isUploadDone": false,
  "createdDateTime": "2026-04-01T18:24:07.1484627Z",
  "stats": {
    "filesUploaded": 1,
    "totalBytesUploaded": 198374
  },
  "data": {
    "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
    "reviewDefinitionId": "f5744a40-bca0-4506-a286-a8afac513d1c",
    "reviewInstanceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8"
  },
  "files": [
    {
      "id": "22125c79-b0fe-4553-8229-6556d85b2561",
      "name": "valid.csv",
      "size": 198374,
      "uploadedDateTime": "2026-04-01T18:42:07.7890258Z"
    }
  ]
}
```
