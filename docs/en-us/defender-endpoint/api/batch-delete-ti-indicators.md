<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/batch-delete-ti-indicators -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Batch Delete Indicators

## API description

Deletes [Indicator](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) entities by ID.

## Limitations

- Rate limitations for this API are 30 calls per minute and 1,500 calls per hour.
- Batch size limit of up to 500 [Indicator](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) IDs.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Ti.ReadWrite.All | 'Read and write Indicators' |

## HTTP request

```http
POST https://api.security.microsoft.com/api/indicators/BatchDelete
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| IndicatorIds | List *String* | A list of the IDs of the indicators to be removed. **Required** |

## Response

- If Indicators all existed and were deleted successfully - 204 OK without content.
- If indicator IDs list is empty or exceeds size limit - 400 Bad Request.
- If any indicator ID is invalid - 400 Bad Request.
- If requestor isn't exposed to any indicator's device groups - 403 Forbidden.
- If any Indicator ID wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
POST https://api.security.microsoft.com/api/indicators/BatchDelete
```

```json
{
    "IndicatorIds": [ "1", "2", "5" ]
}
```
