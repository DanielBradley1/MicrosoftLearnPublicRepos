<!-- Source: https://learn.microsoft.com/en-us/graph/api/investigationoutput-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Get agentic output

Namespace: microsoft.graph

Get the metadata of a stored output owned by an agentic session. This operation uses the [agentic output](https://learn.microsoft.com/en-us/graph/api/resources/investigationoutput?view=graph-rest-beta) resource.

[List the session's outputs](https://learn.microsoft.com/en-us/graph/api/investigationsession-list-outputs?view=graph-rest-beta) to find its output identifiers. Use the returned **id** unchanged for `{output-id}`; treat it as opaque and don't derive it from a filename.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Perception.Read.All | Perception.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Perception.Read.All | Perception.Manage.All |

The signed-in user must have access to the requested resources. Granting an OAuth permission does not override the service's access controls.

## HTTP request

```http
GET /security/agenticSecurity/sessions/{session-id}/outputs/{output-id}
```

## Optional query parameters

This method supports the `$select` OData query parameter. Other query parameters aren't supported.

Use `$select=id` to request only the output identifier without the output category. The identifier can be used in the authenticated **content** route to download the file.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [agentic output](https://learn.microsoft.com/en-us/graph/api/resources/investigationoutput?view=graph-rest-beta) object in the response body.

This response contains metadata, not report bytes. The **content** stream isn't inline in the JSON object. The **kind** property identifies an output category, such as `summary` or `artifact`, not whether a download is shortened.

To [download the file](https://learn.microsoft.com/en-us/graph/api/investigationoutput-get-content?view=graph-rest-beta), use the session **id** and output **id** in `/beta/security/agenticSecurity/sessions/{session-id}/outputs/{output-id}/content`. Send the request with a Microsoft Graph access token authorized for the parent session.

## Examples

The following examples use a fictional session identifier and illustrative metadata. They aren't captured Microsoft Graph responses.

### Example 1: Get output metadata

#### Request

The following example retrieves the executive-summary artifact shown in [List outputs](https://learn.microsoft.com/en-us/graph/api/investigationsession-list-outputs?view=graph-rest-beta).

```http
GET https://graph.microsoft.com/beta/security/agenticSecurity/sessions/6c27d97a-8003-4993-a6e3-e3a8b5a52d50/outputs/c2hhcmVkL291dHB1dHMvcmVwb3J0X2V4ZWN1dGl2ZV9zdW1tYXJ5Lm1k
```

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "c2hhcmVkL291dHB1dHMvcmVwb3J0X2V4ZWN1dGl2ZV9zdW1tYXJ5Lm1k",
  "kind": "artifact"
}
```

### Example 2: Select the output identifier

#### Request

The following example requests only the identifier of an output without its category.

```http
GET https://graph.microsoft.com/beta/security/agenticSecurity/sessions/6c27d97a-8003-4993-a6e3-e3a8b5a52d50/outputs/c2hhcmVkL291dHB1dHMvcmVwb3J0X2V4ZWN1dGl2ZV9zdW1tYXJ5Lm1k?$select=id
```

#### Response

The response contains the selected identifier for the same output. It doesn't contain the file's contents.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "c2hhcmVkL291dHB1dHMvcmVwb3J0X2V4ZWN1dGl2ZV9zdW1tYXJ5Lm1k"
}
```
