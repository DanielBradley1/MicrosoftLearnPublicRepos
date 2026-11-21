<!-- Source: https://learn.microsoft.com/en-us/graph/api/investigationsession-cancel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# investigationSession: cancel

Namespace: microsoft.graph

Request asynchronous cancellation of an agentic session. This operation uses the [agentic session](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta) resource.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Perception.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Perception.Manage.All | Not available. |

The signed-in user must have access to the requested resources. Granting an OAuth permission does not override the service's access controls.

## HTTP request

```http
POST /security/agenticSecurity/sessions/{session-id}/cancel
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `202 Accepted` response code, the current [agentic session](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta), and a `Location` header identifying the session. Acceptance doesn't mean cancellation has completed. Persisted session records aren't deleted.

### Monitor cancellation

[Get the same session](https://learn.microsoft.com/en-us/graph/api/investigationsession-get?view=graph-rest-beta) to check its current state. You can use `$select=id,status,statusDetail` to request the identifier, overall processing status, and substatus. The `Location` URL also identifies this session.

- If **status** is `notStarted` or `running`, cancellation isn't confirmed. Wait before reading the session again rather than polling in a tight loop.
- A canceled session is reported as **status** `failed` with **statusDetail** `stopped`. See the [session lifecycle table](https://learn.microsoft.com/en-us/graph/api/investigationsession-get?view=graph-rest-beta#session-status-and-status-details).
- A `succeeded` session completed successfully; that isn't evidence of cancellation. A `failed` status with another or unavailable detail doesn't, by itself, confirm that cancellation caused the failure.

Use GET requests to monitor progress, not repeated cancellation requests. An HTTP `200 OK` from Get session means the read succeeded, not that cancellation finished. No fixed cancellation duration is implied, and clients must handle unavailable optional detail values.

## Examples

### Request

The following example requests cancellation of a running investigation. The identifiers, session name, and response values are illustrative, not a captured live cancellation.

```http
POST https://graph.microsoft.com/beta/security/agenticSecurity/sessions/6c27d97a-8003-4993-a6e3-e3a8b5a52d50/cancel
```

### Response

The following example shows an accepted request while the session is still running.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/security/agenticSecurity/sessions/6c27d97a-8003-4993-a6e3-e3a8b5a52d50
Content-Type: application/json

{
  "id": "6c27d97a-8003-4993-a6e3-e3a8b5a52d50",
  "status": "running",
  "statusDetail": "inProgress",
  "displayName": "Investigate incident 12345"
}
```
