<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-investigation-collection -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# List Investigations API

## API description

Retrieves a collection of [Investigations](https://learn.microsoft.com/en-us/defender-endpoint/api/investigation).

Supports [OData V4 queries](https://www.odata.org/documentation/). OData supported operators:

- `$filter` on the following properties:

  - `startTime`
  - `id`
  - `state`
  - `machineId`
  - `triggeringAlertId`

- `$stop` with max value of 10,000.
- `$skip`

See examples at [OData queries with Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-odata-samples)

## Limitations

- Maximum page size is 10,000.
- Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: `View Data`. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | `Read and write all alerts` |
| Delegated \(work or school account\) | Alert.ReadWrite | `Read and write alerts` |

## HTTP request

```http
GET https://api.security.microsoft.com/api/investigations
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200, Ok response code with a collection of [Investigations](https://learn.microsoft.com/en-us/defender-endpoint/api/investigation) entities.

## Example

### Request example

Here's an example of a request to get all investigations:

```http
GET https://api.security.microsoft.com/api/investigations
```

### Response example

Here's an example of the response:

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Investigations",
    "value": [
        {
            "id": "63017",
            "startTime": "2020-01-06T14:11:34Z",
            "endTime": null,
            "state": "Running",
            "cancelledBy": null,
            "statusDetails": null,
            "machineId": "a69a22debe5f274d8765ea3c368d00762e057b30",
            "computerDnsName": "desktop-gtrcon0",
            "triggeringAlertId": "da637139166940871892_-598649278"
        }
        ...
    ]
}
```
