<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/cancel-machine-action -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Cancel machine action API

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## API description

Cancel an already launched machine action that isn't yet in final state \(completed, canceled, failed\).

## Limitations

Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.CollectForensics  <br>Machine.Isolate  <br>Machine.RestrictExecution  <br>Machine.Scan  <br>Machine.Offboard  <br>Machine.StopAndQuarantine  <br>Machine.LiveResponse | Collect forensics  <br>Isolate machine  <br>Restrict code execution  <br>Scan machine  <br>Offboard machine  <br>Stop And Quarantine  <br>Run live response on a specific machine |
| Delegated \(work or school account\) | Machine.CollectForensics  <br>Machine.Isolate  <br>Machine.RestrictExecution  <br>Machine.Scan  <br>Machine.Offboard  <br>Machine.StopAndQuarantineMachine.LiveResponse | Collect forensics  <br>Isolate machine  <br>Restrict code execution  <br>Scan machine  <br>Offboard machine  <br>Stop And Quarantine  <br>Run live response on a specific machine |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. Required. |
| Content-Type | string | application/json. Required. |

## Request body

| Parameter | Type | Description |
| --- | --- | --- |
| Comment | String | Comment to associate with the cancellation action. |

## Response

If successful, this method returns 200, OK response code with a Machine Action entity. If machine action entity with the specified id wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```HTTP
POST
https://api.security.microsoft.com/api/machineactions/aaaabbbb-0000-cccc-1111-dddd2222eeee/cancel
```

```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```
