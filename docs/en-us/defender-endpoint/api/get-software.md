<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-software -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# List software inventory API

## API description

Retrieves the organization software inventory.

Supports [OData V4 queries](https://www.odata.org/documentation/). OData supported operators:

- `$filter` on the following properties:

  - `id`
  - `name`
  - `vendor`

- `$top` with max value of 10,000.
- `$skip`

See examples at [OData queries with Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-odata-samples).

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Software.Read.All | 'Read Threat and Vulnerability Management Software information' |
| Delegated \(work or school account\) | Software.Read | 'Read Threat and Vulnerability Management Software information' |

## HTTP request

```http
GET /api/Software
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with the software inventory in the body.

## Example

### Request example

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/Software
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Software",
    "value": [
            {
                "id": "microsoft-_-edge",
                "name": "edge",
                "vendor": "microsoft",
                "weaknesses": 467,
                "publicExploit": true,
                "activeAlert": false,
                "exposedMachines": 172,
                "impactScore": 2.39947438
            }
            ...
        ]
}
```
