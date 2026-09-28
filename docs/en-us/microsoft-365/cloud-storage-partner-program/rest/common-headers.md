<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Standard WOPI request and response headers

Following are the standard WOPI request and response headers.

## GET /wopi/

All WOPI requests might contain the following request and response headers. Individual WOPI operations might send additional request headers or require additional response headers. These unique headers are described in the documentation for each WOPI operation.

Tip

HTTP header names are case-insensitive. For more information, see [**RFC 7230#section-3.2**](https://tools.ietf.org/html/rfc7230.html#section-3.2).

### Request headers

- [*Authorization*](https://tools.ietf.org/html/rfc7235#section-4.2) – The **string** value `Bearer <token>` where `<token>` is the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) for the request.

  Important

  WOPI clients aren't required to pass the [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) in the [**Authorization**](https://tools.ietf.org/html/rfc7235#section-4.2) header, but they must send it as a URL parameter in all WOPI operations. So, for maximum compatibility, WOPI hosts should either use the URL parameter in all cases, or fall back to it if the [**Authorization**](https://tools.ietf.org/html/rfc7235#section-4.2) header isn't included in the request.
- *X-Request-ID* – A **string** that the host should log when logging server activity to correlate that request with a specific WOPI call to the host.
- *X-WOPI-AppEndpoint* – A **string** that indicates the endpoint of the WOPI client sending the request. This is typically used to indicate geographic location, datacenter, and so on. This string mustn't be used for anything other than logging.
- *X-WOPI-RequestingApplication* – A **string** that indicates the WOPI client sending the request. This string mustn't be used for anything other than logging.
- *X-WOPI-ClientVersion* – A **string** that the host should log and which indicates the version of the WOPI client making the request. There's no standard for how this string is formatted, and it mustn't be used for anything other than logging.
- *X-WOPI-CorrelationId* – A **string** that the host should log when logging server activity to correlate that activity with WOPI client activity.

  Tip

  For more information on how this ID is used in Microsoft 365 for the web, see [**Troubleshooting interactions with Microsoft 365 for the web**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/troubleshooting).
- *X-WOPI-DeviceId* – A **string** that the host should log and which indicates the ID of the device making the request. This string mustn't be used for anything other than logging.
- *X-WOPI-SessionId* – A **string** that the host should log to correlate WOPI client activity within a session. This string mustn't be used for anything other than logging.
- *X-WOPI-MachineName* – A **string** indicating the name of the WOPI client machine making the request. This string mustn't be used for anything other than logging.
- *X-WOPI-PerfTraceRequested* – This header is reserved for future use.
- *X-WOPI-Proof* – A **string** representing data signed using a SHA256 \(A 256 bit SHA-2-encoded \[[FIPS 180-2](http://csrc.nist.gov/publications/fips/fips180-2/fips180-2.pdf)\]\) encryption algorithm. For more information on the use of this header value, see [Verifying that requests originate from Microsoft 365 for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys) .
- *X-WOPI-ProofOld* – A **string** representing data signed using a SHA256 \(A 256 bit SHA-2-encoded \[[FIPS 180-2](http://csrc.nist.gov/publications/fips/fips180-2/fips180-2.pdf)\]\) encryption algorithm. For more information on the use of this header value, see [Verifying that requests originate from Microsoft 365 for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys).
- *X-WOPI-TimeStamp* – A **64-bit integer** that represents the number of 100-nanosecond intervals that have elapsed between 12:00:00 midnight, January 1, 0001, and the time of the request. You can set this value in .NET using the following C# code: `DateTime.UtcNow.Ticks`.

For more information, see [**DateTime.Ticks Property**](https://msdn.microsoft.com/library/cc319699.aspx).

### Response headers

- [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – This header should be set to a value appropriate to the type of data being included in the response. For example, when responding to a WOPI request with JSON-encoded data in the response body, the [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) header should be set to `application/json`. WOPI clients might ignore a response with a [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) header that doesn't match the expected type.
- *X-WOPI-HostEndpoint* – A **string** that indicates the endpoint of the WOPI host handling the request. This is analogous to the **X-WOPI-AppEndpoint** request header and typically indicates geographic location, datacenter, and so on. This string mustn't be used for anything other than logging.
- *X-WOPI-MachineName* – A **string** indicating the name of the WOPI host server handling the request. This string mustn't be used for anything other than logging.
- *X-WOPI-PerfTrace* – This header is reserved for future use.
- *X-WOPI-ServerError* – A **string** indicating that an error occurred while processing the WOPI request. This header should be included in a WOPI response if the status code is [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1), but might be returned on any response with a non-200 status code. The value should contain details about the error. This string mustn't be used for anything other than logging.
- *X-WOPI-ServerVersion* – A **string** indicating the version of the WOPI host server handling the request. There's no standard for how this string is formatted, and it must not be used for anything other than logging.
