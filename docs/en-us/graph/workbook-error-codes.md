<!-- Source: https://learn.microsoft.com/en-us/graph/workbook-error-codes -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Error codes for workbooks and charts APIs

This article describes error codes that are returned by the workbooks and charts APIs in Microsoft Graph when a request sent through these APIs fails. For details about handling error responses from workbooks and charts APIs in Microsoft Graph, see [Error handling for Excel APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/workbook-error-handling). For more information about error responses and resource types in Microsoft Graph, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Error codes and messages

The following table lists the current error codes and messages. The service might add new error codes at any time.

| Status Code | Error Code | Error Message |
| :--- | :--- | :--- |
| 400 | `badRequest` | The request is malformed or incorrect. |
| 401 | `unauthorized` | The caller isn't authenticated. |
| 403 | `forbidden` | The caller doesn't have permission to perform the action. |
| 404 | `notFound` | The resource couldn't be found. |
| 405 | `methodNotAllowed` | The HTTP method in the request isn't allowed on the resource. |
| 409 | `conflict` | The current state conflicts with what the request expects. |
| 413 | `payloadTooLarge` | The request size exceeds the maximum limit. |
| 429 | `tooManyRequests` | The app or user has been throttled. |
| 500 | `internalServerError` | An internal server error occurred while processing the request. |
| 501 | `notImplemented` | The requested feature isn’t implemented. |
| 502 | `badGateway` | The server encountered a temporary error and couldn't complete your request. |
| 503 | `serviceUnavailable` | The service isn't available. Try your request again. |
| 504 | `gatewayTimeout` | The server, while acting as a proxy, didn't receive a timely response from the upstream server in order to complete the request. |

## Detailed error codes

The following are required error codes that your app might encounter within the first-level of nested **innerError** objects. The service might add new error codes at any time.

- `accessConflict`
- `badRequestUncategorized`
- `conflictUncategorized`
- `forbiddenUncategorized`
- `gatewayTimeoutUncategorized`
- `internalServerErrorUncategorized`
- `invalidSessionAccessConflict`
- `invalidSessionAuthentication`
- `invalidSessionNotFound`
- `invalidSessionReCreatable`
- `invalidSessionRestricted`
- `invalidSessionUnexpected`
- `invalidSessionUnsupportedWorkbook`
- `methodNotAllowedUncategorized`
- `notFoundUncategorized`
- `notImplementedUncategorized`
- `payloadTooLargeUncategorized`
- `serviceUnavailableUncategorized`
- `tooManyRequestsUncategorized`
- `transientFailure`
- `unauthorizedUncategorized`
- `unsupportedWorkbook`

For examples of optional error codes within the first-level of nested **innerError** objects, see [Optional second-level error code examples](https://learn.microsoft.com/en-us/graph/workbook-error-handling#optional-second-level-error-code-examples).

Note

The **innerError** object might recursively contain more deeper **innerError** objects with additional, more specific error codes. These deeper **innerError** codes are intended for diagnostics purpose only.

## Related content

- [Use the Excel REST API](https://learn.microsoft.com/en-us/graph/api/resources/excel)
