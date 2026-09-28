<!-- Source: https://learn.microsoft.com/en-us/graph/api/trustframeworkkey_v2-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update trustFrameworkKey\_v2

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [trustFrameworkKey\_v2](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey_v2?view=graph-rest-beta) object. Only Status Property is allowed to update from this request.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TrustFrameworkKeySet.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TrustFrameworkKeySet.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *B2C IEF Keyset Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /trustFramework/keySets/{trustFrameworkKeySetId}/keys_v2/{trustFrameworkKey_v2Id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| status | trustFrameworkKeyStatus | Status of the key. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `204 No Content` response code and an updated [trustFrameworkKey\_v2](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey_v2?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/trustFramework/keySets/{trustFrameworkKeySetId}/keys_v2/aTREvwojOB9ph3fr2r6eTf_5eD5fmQsfsapVMwYI3o
Content-Type: application/json

{
  "status": "enabled"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const trustFrameworkKey_v2 = {
  status: 'enabled'
};

await client.api('/trustFramework/keySets/{trustFrameworkKeySetId}/keys_v2/aTREvwojOB9ph3fr2r6eTf_5eD5fmQsfsapVMwYI3o')
	.version('beta')
	.update(trustFrameworkKey_v2);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
