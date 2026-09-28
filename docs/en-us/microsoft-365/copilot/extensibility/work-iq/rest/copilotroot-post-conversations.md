<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotroot-post-conversations -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Work IQ - Create copilotConversation

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications isn't supported.

The Work IQ Chat API allows you to create and continue multi-turn conversations with Microsoft 365 Copilot, while respecting the defined access controls within the organization. Use the Chat API to integrate Microsoft 365 Copilot into your generative AI solutions.

This documentation covers creating Copilot conversations using the Chat API. Learn how to continue [synchronous conversations](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chat) or [streamed conversations](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chatoverstream) with the Chat API.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions only if your app requires it. To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/permissions).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WorkIQAgent.Ask | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST https://workiq.svc.cloud.microsoft/rest/conversations
```

```http
POST https://workiq.svc.cloud.microsoft/rest/beta/conversations
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. |
| `Content-Type` | `application/json.` Required. |

## Request body

In the request body, supply an empty JSON body.

## Response

If successful, this action returns a `201 Created` response code and a [copilotConversation](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/resources/copilotconversation) in the response body.

## Example

The following example shows how to create a Copilot conversation through the Work IQ Chat API. Once the conversation is created, the `id` in the response body is used as a path parameter for continuing the conversation, using either the synchronous endpoint or the streamed endpoint.

### Request

The following example shows the request.

```http
POST https://workiq.svc.cloud.microsoft/rest/conversations
Content-Type: application/json

{}
```

```http
POST https://workiq.svc.cloud.microsoft/rest/beta/conversations
Content-Type: application/json

{}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0d110e7e-2b7e-4270-a899-fd2af6fde333",
  "createdDateTime": "2025-09-30T15:28:46.1560062Z",
  "displayName": "",
  "status": "active",
  "turnCount": 0
}
```

## Related content

- [Overview of the Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/overview)
- [Work IQ Samples](https://github.com/microsoft/work-iq-samples)
- [Continue synchronous conversations with Microsoft 365 Copilot using the Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chat)
- [Continue streamed conversations with Microsoft 365 Copilot using the Work IQ Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/rest/copilotconversation-chatoverstream)
