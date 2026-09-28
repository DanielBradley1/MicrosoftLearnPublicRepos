<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# Update ediscoveryReviewSet

Namespace: microsoft.graph.security

Update the properties of an [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to access review sets in eDiscovery cases they create and are members of. **This is the least privileged option for accessing review sets in their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access review sets in all eDiscovery cases in the organization.
- **Reviewer**. Provides read-only access to review sets within eDiscovery cases where the user is a member. Reviewers can view and tag documents but cannot perform other case management tasks.

The Review role allows users to access review sets in eDiscovery cases they are members of. Users can view and tag documents in review sets but cannot preview search results or perform other search or case management tasks.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
PATCH /security/cases/ediscoveryCases/{ediscoverycaseId}/reviewSets/{reviewSetId}
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
| description | String | The description of the review set. Optional. |
| displayName | String | The name of the review set. The name is unique with a maximum limit of 64 characters. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request that updates the review set name to `reviewset01` and the description to `reviewset description`.

```http
PATCH https://graph.microsoft.com/v1.0/security/cases/ff8b82a4-071c-43c7-b0f4-a2708a8736c0/reviewSets/a5658335-7242-4550-ad22-e57b443f7442
Content-Type: application/json

{
  "displayName": "reviewset01",
  "description": "reviewset description"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
