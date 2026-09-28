<!-- Source: https://learn.microsoft.com/en-us/graph/api/get-device-command-status?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Get device command status \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the status of a command on a device. For the full list of status codes, see [List of actionStatus](#list-of-actionstatus).

Caution

This API is deprecated and stopped returning data on September 30, 2020.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Device.Command | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET me/devices/{id}/commands/{id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Response

```http
HTTP/1.1 200 OK
```

```json
  {
    "id": "0",
    "status": "requesting",
    "type": "null",
    "appServiceName": "null",
    "packageFamilyName": "null",
    "error": "null",
    "responsepayload": "null",
    "payload": "null",
    "permissionTicket": "null",
    "postBackUri": "null"
  }
```

## List of actionStatus

- requesting, // Command has been created and is waiting to be processed
- sentToTarget, // Command has been sent to the target device
- executing, // Target device acknowledged receipt of the command and is executing it
- completed, // Command execution completed
- failedToSend, // Service failed to send command to target device
- executionFailed, // Command execution failed
- commandDropped, // Command dropped by client if device is in ConnectedStandby state
- cancel, // Cancel the command
- cancelling, // Cancelling the command
- canceled, // Command has been cancelled
- retry, // Service is retrying to send command to target
- expired, // Command processing exceeded expiry time
- error, // Internal error while processing the command
- custom // Custom status

## Example

In this example, you need the ID of the device and the ID of the command that was issued to the device. The device ID is returned when issuing a GET call to `/me/devices`, and the command ID is returned when doing a POST call on `/me/devices/{id}/command`.

#### Request

The following example shows the request.

```http
GET me/devices/{id}/commands/{id}
Authorization: Bearer Eaeou....
Content-Type: application/json; charset=utf-8
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "value":
  {
    "id": "0158355AD4D680CC4E2994CC009EFFD7337D1335FCA6ED266…",
    "status": "completed",
    "type": null,
    "appServiceName": null,
    "packageFamilyName": null,
    "error": null,
    "permissionTicket": null,
    "postBackUri": null,
    "payload": null
  }
}
```

## Get command payload

Get a response payload for a specific action on a device. The response payload is used when querying an app service to carry data back.

### Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Not supported. |
| Delegated \(personal Microsoft account\) | Device.Command |
| Application | Not supported. |

### HTTP request

```http
GET me/devices/{id}/commands/{id}/responsePayload
```

### Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

### Response

```http
HTTP/1.1 200 OK
```

```json
{
  "@odata.context": "https://graph.microsoft.com/devices/$metadata#microsoft.graph.PayloadResponse",
  "MsIgnoredParameter":0,
  "CreationDate":"date-time",
  "Type":"Ok"
}
```

### Example

In this example, you need the ID of the device and the ID of the command that was issued to the device. The device ID is returned when issuing a GET call on `/me/devices`, and the command ID is returned when doing a POST call on `/me/devices/{id}/command`.

#### Request

The following example shows the request.

```http
GET me/devices/{id}/commands/{id}
Authorization: Bearer Eaeou....
Content-Type: application/json; charset=utf-8
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "@odata.context": "https://graph.microsoft.com/devices/$metadata#microsoft.graph.PayloadResponse",
  "MsIgnoredParameter":0,
  "CreationDate":"04/27/2017",
  "Type":"Ok"
}
```
