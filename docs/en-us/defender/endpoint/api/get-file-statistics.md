<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-file-statistics -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get file statistics API

## API description

Retrieves the statistics for the given file.

## Limitations

- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.
- The maximum value for `lookbackhours` is 720 Hours\(30 days\).

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | File.Read.All | 'Read file profiles' |
| Delegated \(work or school account\) | File.Read.All | 'Read file profiles' |

## HTTP request

```http
GET /api/files/{id}/stats
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request URI parameters

| Name | Type | Description |
| --- | --- | --- |
| lookBackHours | Int32 | Defines the hours we search back to get the statistics. Defaults to 30 days. **Optional**. |

## Request body

Empty

## Response

If successful and file exists - 200 OK with statistical data in the body. If file does not exist - 404 Not Found.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/files/0991a395da64e1c5fbe8732ed11e6be064081d9f/stats?lookBackHours=48
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgFileStats",
    "sha1": "0991a395da64e1c5fbe8732ed11e6be064081d9f",
    "organizationPrevalence": 14850,
    "orgFirstSeen": "2019-12-07T13:44:16Z",
    "orgLastSeen": "2020-01-06T13:39:36Z",
    "globallyPrevalence": 705012,
    "globalFirstObserved": "2015-03-19T12:20:07.3432441Z",
    "globalLastObserved": "2020-01-06T13:39:36Z",
    "topFileNames": [
        "MREC.exe"
    ]
}
```
