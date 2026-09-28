<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-post-sensorcandidateactivationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# Update sensorCandidateActivationConfiguration

Namespace: microsoft.graph.security

Update a [sensorCandidateActivationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesSensors.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesSensors.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned the *Security Administrator* [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with supported permissions created through the Microsoft Defender XDR Unified Role-Based Access Control \(RBAC\).

## HTTP request

```http
POST /security/identities/sensorCandidateActivationConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.sensorCandidateActivationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorcandidateactivationconfiguration?view=graph-rest-1.0) object.

You can specify the following properties when creating a **sensorCandidateActivationConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| activationMode | microsoft.graph.security.sensorCandidateActivationMode | The activation mode for the sensor candidate. The possible values are: `manual` and `automated`. Required. |

## Response

If successful, this method returns a `200 OK` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/security/identities/sensorCandidateActivationConfigurations
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.sensorCandidateActivationConfiguration",
  "activationMode": "automated"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
```
