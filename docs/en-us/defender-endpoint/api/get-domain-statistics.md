<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-domain-statistics -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get domain statistics API

## API description

Retrieves the statistics on the given domain.

## Limitations

- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.
- The maximum value for `lookbackhours` is 720 hours \(30 days\).

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | URL.Read.All | 'Read URLs' |
| Delegated \(work or school account\) | URL.Read.All | 'Read URLs' |

## HTTP request

```http
GET /api/domains/{domain}/stats
```

## Request headers

| Header | Value |
| --- | --- |
| Authorization | Bearer {token}. **Required**. |

## Request URI parameters

| Name | Type | Description |
| --- | --- | --- |
| lookBackHours | Int32 | Defines the hours we search back to get the statistics. Defaults to 30 days. **Optional**. |

## Request body

Empty

## Response

If successful and domain exists - 200 OK, with statistics object in the response body. If domain doesn't exist - 200 OK with a prevalence set to 0.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/domains/example.com/stats?lookBackHours=48
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgDomainStats",
    "host": "example.com",
    "organizationPrevalence": 4070,
    "orgFirstSeen": "2017-07-30T13:23:48Z",
    "orgLastSeen": "2017-08-29T13:09:05Z"
}
```
