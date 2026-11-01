<!-- Source: https://learn.microsoft.com/en-us/graph/api/federatedtokenvalidationpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Update federatedTokenValidationPolicy

Namespace: microsoft.graph

Update the properties of a [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.FedTokenValidation | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.FedTokenValidation | Not available. |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. The following privileged roles are supported for this operation:

- Security Administrator
- Hybrid Identity Administrator
- External Identity Provider Administrator

## HTTP request

```http
PUT /policies/federatedTokenValidationPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

Important

If you set `rootDomains` to `enumerated` or `allManagedAndEnumeratedFederated`, you must specify `@odata.type` as `#microsoft.graph.enumeratedDomains` on the **validatingDomains** property. Omitting the discriminator in these cases returns `HTTP 400 Bad Request`.

For any other `rootDomains` value \(`none`, `all`, `allFederated`, `allManaged`\), the subtype is inferred as `microsoft.graph.allDomains`, so `@odata.type` is optional.

| Property | Type | Description |
| :--- | :--- | :--- |
| validatingDomains | [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0) | Verified domains that Microsoft Entra validates whether the federated account's root domain matches with the mapped Microsoft Entra account's root domain. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PUT https://graph.microsoft.com/v1.0/policies/federatedTokenValidationPolicy
Content-Type: application/json

{
  "validatingDomains": {
    "@odata.type": "#microsoft.graph.enumeratedDomains",
    "rootDomains": "enumerated",
    "domainNames": ["contoso.com", "fabrikam.com"]
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
  "@odata.type": "#microsoft.graph.federatedTokenValidationPolicy",
  "id": "932b8f7f-68c1-6fe5-59ab-56e1ff752f30",
  "deletedDateTime": null,
  "validatingDomains": {
    "@odata.type": "#microsoft.graph.enumeratedDomains",
    "rootDomains": "enumerated",
    "domainNames": ["contoso.com", "fabrikam.com"]
  }
}
```
