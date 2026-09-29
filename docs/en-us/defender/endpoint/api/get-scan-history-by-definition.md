<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-scan-history-by-definition -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Get scan history by definition

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## API description

Retrieves a list of the scan history by definitions.

Supports [OData V4 queries](https://www.odata.org/documentation/). OData supported operators:

- `$top` with max value of 10,000.
- `$skip`

For an example of OData operation usage, see [example $top request](#example-top-request).

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials, to view data, the user needs to have at least the following role permission: `ViewData` or `TvmViewData` . For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.Read.All | Read all scan information. |
| Delegated \(work or school account\) | Machine.Read.All | Read all scan information. |

## HTTP request

```http
POST api/DeviceAuthenticatedScanDefinitions/GetScanHistoryByScanDefinitionId
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | string | application/json. **Required**. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| ScanDefinitionIds | String | The scan Id. **Required**. |

## Response

If successful, this method returns 200 - OK response code with a list of the scan history by definition.

## Example request

Here's an example of the request.

```http
POST https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryByScanDefinitionId
```

```json
{
    "ScanDefinitionIds": ["4ad8d463-6b3a-4894-b42a-a2de9ea0a8ae", "60c4aa57-c573-4488-8d18-230914792a92", "c6220f67-2cad-4ba3-a2fa-7ded6384da56"]
}
```

## Response example

```json
{
"@odata.context": "https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryByScanDefinitionId",
    "value": [
    {
    "ScanDefinitionIds": "4ad8d463-6b3a-4894-b42a-a2de9ea0a8ae",
    "LastScanned": "2022-12-20T11:14:24.5561791Z",
    "ScanStatus": "Partial Success",
    "ScannerId": "625431694b7d2ca9d07e77ca1b029ef216bebb6d"
    },
    {
    "ScanDefinitionIds": "60c4aa57-c573-4488-8d18-230914792a92",
    "LastScanned": "2022-11-17T15:13:24.5561791Z",
    "ScanStatus": "Partial Success",
    "ScannerId": "625431694b7d2ca9d07e77ca1b029ef216bebb6d"
    },
    {
    "ScanDefinitionIds": "c6220f67-2cad-4ba3-a2fa-7ded6384da56",
    "LastScanned": "2022-11-10T18:15:24.5561791Z",
    "ScanStatus": "Partial Success",
    "ScannerId": "625431694b7d2ca9d07e77ca1b029ef216bebb6d"
    },
   ]
}
```

## Example $top request

Here's an example of a request that returns only 1 session.

```http
POST https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryByScanDefinitionId?$top=1
```

## $top Response example

```json
{
"@odata.context": "https://api.security.microsoft.com/api/DeviceAuthenticatedScanDefinitions/GetScanHistoryByScanDefinitionId",
    "value": [
    {
    "ScanDefinitionIds": "4ad8d463-6b3a-4894-b42a-a2de9ea0a8ae",
    "LastScanned": "2022-12-20T11:14:24.5561791Z",
    "ScanStatus": "Partial Success",
    "ScannerId": "625431694b7d2ca9d07e77ca1b029ef216bebb6d"
    },
 ]
}
```
