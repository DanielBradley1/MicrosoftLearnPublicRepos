<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-emailthreatsubmission-review?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# emailThreatSubmission: review

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Review a threat submission. Only [emailThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-emailthreatsubmission?view=graph-rest-beta) objects submitted by end users support the review action.

Review actions for [urlThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-urlthreatsubmission?view=graph-rest-beta) and [fileThreatSubmission](https://learn.microsoft.com/en-us/graph/api/resources/security-filethreatsubmission?view=graph-rest-beta) objects are not supported for end user.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatSubmission.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatSubmission.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/threatSubmission/emailThreats/{emailThreatsId}/review
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| category | String | The email is being reported as notSpam, junk, phishing, malware. Case insensitive. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/security/threatSubmission/emailThreats/49c5ef5b-1f65-444a-e6b9-08d772ea2059/review
Content-type: application/json

{
  "category": "phishing"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const review = {
  category: 'phishing'
};

await client.api('/security/threatSubmission/emailThreats/49c5ef5b-1f65-444a-e6b9-08d772ea2059/review')
	.version('beta')
	.post(review);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
