<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Get sensitivityLabel

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of a [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | InformationProtectionPolicy.Read | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | InformationProtectionPolicy.Read.All | Not available. |

## HTTP request

To get a label as the signed-in user \(delegated permission\) or a specified user \(application permission\):

```http
GET /users/{usersId}/security/informationProtection/sensitivityLabels/{sensitivityLabelId}
GET /me/security/informationProtection/sensitivityLabels/{sensitivityLabelId}
```

To get labels available to the organization as a service principal \(application permission\):

```http
GET /security/informationProtection/sensitivityLabels/{sensitivityLabelId}
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is `ApplicationName/Version`. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/users/bob@contoso.com/security/informationProtection/sensitivityLabel/5aa3cb3c-f0bd-9d1f-bc54-af399bed88e2
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('bob%40contoso.com')/security/informationProtection/sensitivityLabels/$entity",
    "id": "0ed12617-d0ef-4053-b8e4-ecf5bcf2ffb3",
    "name": "FTEs, Approved Partners, and Vendors",
    "description": "",
    "color": "",
    "sensitivity": 2,
    "tooltip": "This label is intended to protect NDA-level data and share with external and internal vendors and partners, as well as all FTEs. FTEs will have full control of the protected information.",
    "isActive": true,
    "isAppliable": true,
    "contentFormats": [
        "file",
        "email",
        "site",
        "unifiedgroup",
        "schematizeddata"
    ],
    "hasProtection": true
}
```
