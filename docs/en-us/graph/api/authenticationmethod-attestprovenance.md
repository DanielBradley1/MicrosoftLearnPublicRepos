<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethod-attestprovenance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# authenticationMethod: attestProvenance

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Apply an administrative attestation to the [credential provenance](https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta) of an [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-beta).

Credential provenance is currently supported for FIDO2 authentication methods. Classification, actor information, and timestamps are managed by the service and aren't request parameters.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CredentialProvenance.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CredentialProvenance.ReadWrite.All | Not available. |

## HTTP request

```http
POST /users/{user-id}/authentication/methods/{authenticationMethod-id}/attestProvenance
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attestationReason | String | Required. The explanation for the administrative attestation. |
| verificationEventId | String | Required. The identifier of the user's [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) associated with the attestation. |

## Response

If successful, this action returns a `200 OK` response code and a [credentialProvenance](https://learn.microsoft.com/en-us/graph/api/resources/credentialprovenance?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Attest credential provenance

#### Request

The following example attests the provenance of a user's FIDO2 authentication method.

```http
POST https://graph.microsoft.com/beta/users/c2b3a4d5-6e7f-4890-a123-4567890abcde/authentication/methods/-2_GRUg2-HYz6_1YG4YRAQ2/attestProvenance
Content-Type: application/json

{
  "attestationReason": "In-person identity proofing confirmed by help desk",
  "verificationEventId": "9c2d5e61-1a3b-4a2f-9f6e-2f8b6c4d91aa"
}
```

#### Response

The following example shows the response, shortened to show the server-recorded actor information.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.credentialProvenance",
  "assertedBy": {
    "actorType": "user",
    "actorId": "84fd0782-d012-4b54-9a6c-16e52413f6de"
  }
}
```
