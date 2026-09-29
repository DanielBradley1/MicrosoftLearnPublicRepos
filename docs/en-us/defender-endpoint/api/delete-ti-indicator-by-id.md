<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/delete-ti-indicator-by-id -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Delete Indicator API

## API description

Deletes an [Indicator](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) entity by ID.

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Ti.ReadWrite.All | 'Read and write Indicators' |

## HTTP request

```http
Delete https://api.security.microsoft.com/api/indicators/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If Indicator exists and deleted successfully - 204 OK without content.

If Indicator with the specified ID wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
DELETE https://api.security.microsoft.com/api/indicators/995
```
