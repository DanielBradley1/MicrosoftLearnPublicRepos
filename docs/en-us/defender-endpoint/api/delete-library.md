<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/delete-library -->
<!-- Sitemap-Last-Modified: 2026-02-17 -->

# Delete a file from the live response library

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## API description

Delete a file from live response library.

Tip

You can also delete live response files from the [Library management](https://learn.microsoft.com/en-us/defender-endpoint/configure-libraries-live-response) page in the Microsoft Defender portal.

## Limitations

Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Library.Manage | Manage live response library |
| Delegated \(work or school account\) | Library.Manage | Manage live response library |

## HTTP request

DELETE [https://api.security.microsoft.com/api/libraryfiles/{fileName}](https://api.security.microsoft.com/api/libraryfiles/%7BfileName%7D)

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer<token>. **Required**. |

## Request body

Empty

## Response

- If file exists in library and deleted successfully 204 No Content.
- If specified file name was not found 404 Not Found.

## Example

Request

Here is an example of the request.

```http
DELETE https://api.security.microsoft.com/api/libraryfiles/script1.ps1
```
