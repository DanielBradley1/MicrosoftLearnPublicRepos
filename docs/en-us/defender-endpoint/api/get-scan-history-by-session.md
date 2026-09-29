<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-scan-history-by-session -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get scan history by session

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## API description

Retrieves a list of the scan history by session.

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- To view data the user needs to have at least the following role permission: `ViewData` or `TvmViewData`. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.Read.All | Read all scan information. |
| Delegated \(work or school account\) | Machine.Read.All | Read all scan information. |

## HTTP request

```http
POST /api/DeviceAuthenticatedScanDefinitions/GetScanHistoryBySessionId
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | string | Bearer {token}. **Required**. |
| Content-Type | string | application/json. **Required**. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| SessionIds | String | The session Id. **Required**. |

## Response

If successful, this method returns 200 - OK response code with a list of the scan history for a session.

## Example request

Here's an example of the request.

```http
POST https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryBySessionId
```

```json
{
    "SessionIds": ["01decc497f4b4ec49a5fc4e12597f8c8"]
}
```

## Response example

```json
{
 "@odata.context": "https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryBySessionId",
    "value": [
    {
     "orgId": "asdf781a0c-792d-46d3-bbea-a93dbc0bfcaa",
     "ScanDefinitionIds": "4ad8d463-6b3a-4894-b42a-a2de9ea0a8ae",
     "SessionIds": "01decc497f4b4ec49a5fc4e12597f8c8",
     "NumberOfSuccessfullyScannedTargets": 3,
     "NumberOfTargets": 3,
     "ScanStatus": "Success",
     "LastScanned": "2022-12-19T15:14:24.5561791Z",
     "ListScannedTargets": {
         "Ip": "127.0.0.1",
         "Hostname": "DESKTOP-Test",
         "ScannedDeviceDescription": "Network device",
         "ErrorMessage": "",
         "ScanStatus": "Success",
         "ScanDuration": "00:08:30",
        },
        {
         "Ip": "127.0.0.2",
         "Hostname": "DESKTOP-Test2",
         "ScannedDeviceDescription": "Network device 2",
         "ErrorMessage": "",
         "ScanStatus": "Success",
         "ScanDuration": "00:08:00",
        },
{
         "Ip": "127.0.0.3",
         "Hostname": "DESKTOP-Test3",
         "ScannedDeviceDescription": "Network device 3",
         "ErrorMessage": "",
         "ScanStatus": "Success",
         "ScanDuration": "00:08:50",
        },
    }
  ]
}
```
