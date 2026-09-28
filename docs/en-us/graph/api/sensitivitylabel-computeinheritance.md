<!-- Source: https://learn.microsoft.com/en-us/graph/api/sensitivitylabel-computeinheritance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# sensitivityLabel: computeInheritance

Namespace: microsoft.graph

Calculate the sensitivity label that should be inherited by an output artifact, given a set of sensitivity labels from input or referenced artifacts.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SensitivityLabel.Evaluate | SensitivityLabel.Evaluate.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SensitivityLabel.Evaluate | SensitivityLabel.Evaluate.All |

## HTTP request

```http
GET /security/dataSecurityAndGovernance/sensitivityLabels/computeInheritance
```

## Filter parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| applicableTo | String | Optional. A comma-separated string of content formats \(for example, `file, email`\). Filters the returned labels to only those applicable to *at least one* of the specified formats. Possible values are `email`, `file`, `schematizedData`, `site`, `teamwork`, `unifiedGroup`. |
| locale | String | Optional. Specifies the locale for localizable fields. |
| labelIds | Collection of Strings | Optional. A collection of comma-separated string of sensitivity label GUIDs. Filters the returned labels to only those matching the specified IDs. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Client-Request-Id | Optional. A client-generated GUID to trace the request. Recommended for troubleshooting. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a single [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-1.0) object in the response body, representing the calculated inherited label.

If no applicable label is found based on the input and filters, or if an error occurs \(for example, invalid label ID provided\), the API might return an error response \(for example, `400 Bad Request` or `404 Not Found`\) with details in an [error object](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Request

The following example shows a request to compute the inherited label from input label, considering only labels applicable to the `File` content format.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/sensitivityLabels/computeInheritance(labelIds=["4e4234dd-377b-42a3-935b-0e42f138fa23"],locale='en-US',contentFormats=["File"])
Authorization: Bearer {token}
Content-Type: application/json
Client-Request-Id: c5e4d3b2-a1f0-e9d8-c7b6-a5e4d3b2a1f0

"4e4234dd-377b-42a3-935b-0e42f138fa23"  // General (Sensitivity 10, File/Email)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sensitivityLabel = await client.api('/security/dataSecurityAndGovernance/sensitivityLabels/computeInheritance(labelIds=["4e4234dd-377b-42a3-935b-0e42f138fa23"],locale='en-US',contentFormats=["File"])')
	.header('Authorization','Bearer {token}')
	.header('Client-Request-Id','c5e4d3b2-a1f0-e9d8-c7b6-a5e4d3b2a1f0')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. The **confidential** label is returned because it's the most sensitive label among the inputs that supports the `File` content format.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.security.sensitivityLabel",
  "id": "a7a21bba-8197-491f-a5d6-0d0f955397cf",
  "name": "Confidential",
  "description": "Confidential data.",
  "color": "#ff0000",
  "priority": 0,
  "toolTip": "Data that requires protection.",
  "isEnabled": true,
  "isEndpointProtectionEnabled": true,
  "autoTooltip": "",
  "actionSource": "manual",
  "applicableTo": "email,teamwork,file",
  "sublabels": []
}
```
