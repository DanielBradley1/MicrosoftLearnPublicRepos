<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-ti-indicators-collection -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# List Indicators API

## API description

Retrieves a collection of all active [Indicators](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator).

Supports [OData V4 queries](https://www.odata.org/documentation/). OData supported operators:

- `$filter` on the following operators: `application`

  - `createdByDisplayName`
  - `expirationTime`
  - `generateAlert`
  - `title`
  - `rbacGroupNames`
  - `rbacGroupIds`
  - `indicatorValue`
  - `indicatorType`
  - `creationTimeDateTimeUtc`
  - `createdBy`
  - `action`
  - `severity`

- `$top` with max value of 10,000.
- `$skip`

See examples at [OData queries with Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-odata-samples).

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Ti.ReadWrite | `Read and write Indicators` |
| Application | Ti.ReadWrite.All | `Read and write All Indicators` |
| Delegated \(work or school account\) | Ti.ReadWrite | `Read and write Indicators` |

## HTTP request

```http
GET https://api.security.microsoft.com/api/indicators
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200, Ok response code with a collection of [Indicator](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) entities.

If the Application has `Ti.ReadWrite.All` permission, it will be exposed to all Indicators. Otherwise, it will be exposed only to the Indicators it created.

## Example 1

### Example 1 request

Here's an example of a request that gets all indicators.

```http
GET https://api.security.microsoft.com/api/indicators
```

### Example 1 response

Here's an example of the response.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "995",
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "action": "Alert",
            "application": "demo-test",
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
            "rbacGroupNames": []
        },
        {
            "id": "996",
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```

## Example 2

### Example 2 request

Here's an example of a request that gets all Indicators with `AlertAndBlock` action.

```http
GET https://api.security.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### Example 2 response

Here's an example of the response.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "997",
            "indicatorValue": "111e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```
