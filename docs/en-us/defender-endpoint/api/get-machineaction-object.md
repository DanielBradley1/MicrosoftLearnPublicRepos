<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machineaction-object -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get machineAction API

## API description

Retrieves specific [Machine Action](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) by its ID.

## Limitations

- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
GET https://api.security.microsoft.com/api/machineactions/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200, Ok response code with a [Machine Action](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) entity. If machine action entity with the specified ID wasn't found - 404 Not Found.

## Example

### Example request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/machineactions/aaaabbbb-0000-cccc-1111-dddd2222eeee
```

### Response example

Here's an example of the response.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
    "type": "Isolate",
    "scope": "Selective",
    "requestor": "Analyst@TestPrd.onmicrosoft.com",
    "requestorComment": "test for docs",
    "status": "Succeeded",
    "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
    "computerDnsName": "desktop-test",
    "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
    "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
    "relatedFileInfo": null
}
```
