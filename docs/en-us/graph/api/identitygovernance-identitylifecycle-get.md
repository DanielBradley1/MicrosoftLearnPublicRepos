<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-identitylifecycle-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Get identityLifecycle

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of an [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) object for a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta). Use `$expand=effectiveGoverningPolicy` to retrieve the highest-priority policy governing the identity. The **lastAttestationDateTime** property can be `null` for an identity that hasn't yet been attested.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /servicePrincipals/{servicePrincipalsId}/lifecycle
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/servicePrincipals/55bc54bb-f5ef-431b-9e8f-6ee6320191fe/lifecycle
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecycle",
  "id": "55bc54bb-f5ef-431b-9e8f-6ee6320191fe",
  "lastAttestationDateTime": "2026-06-01T12:00:00Z",
  "effectiveGoverningPolicy": {
    "id": "f360e310-e2c9-4bb3-a3ca-791d3c0b6548"
  },
  "complianceIssues": [
    {
      "@odata.type": "#microsoft.graph.identityGovernance.attestationComplianceIssue",
      "issueCode": "SponsorCountBelowMinimum",
      "description": "The agent identity does not meet the minimum sponsor count requirement.",
      "governingPolicyReferenceId": "f360e310-e2c9-4bb3-a3ca-791d3c0b6548",
      "ruleType": "sponsorPresence",
      "attestationBlockReasons": ["MissingRequiredNumberOfSponsors"]
    }
  ]
}
```
