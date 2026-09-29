<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machines-by-software -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List devices by software

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieve a list of device references that has this software installed.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Software.Read.All | 'Read Threat and Vulnerability Management Software information' |
| Delegated \(work or school account\) | Software.Read | 'Read Threat and Vulnerability Management Software information' |

## HTTP request

```http
GET /api/Software/{Id}/machineReferences
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}.**Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK and a list of devices with the software installed in the body.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/Software/microsoft-_-edge/machineReferences
```

### Response example

Here`s an example of the response.

```json

{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "7c7e1896fa39efb0a32a2cf421d837af1b9bf762",
            "computerDnsName": "dave_desktop",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        },
        {
            "id": "7d5cc2e7c305e4a0a290392abf6707f9888fda0d",
            "computerDnsName": "jane_PC",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```
