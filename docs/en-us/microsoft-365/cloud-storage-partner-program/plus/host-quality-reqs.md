<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/host-quality-reqs -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# CSPP Plus Host Quality Requirements

The quality metrics described below should be monitored by CSPP Plus hosts on an ongoing basis to ensure a quality end-to-end experience for Office customers.

## Reliability

Microsoft and each CSPP Plus host will measure the reliability of the host and sync-client integration at the API layer.

#### Host API Reliability

The host APIs are documented in this documentation set, including the CSPP Plus WOPI extensions.

The host must deliver a highly reliable service before the end-to-end experience is generally available:

- 99.95% reliable per API
- All APIs included
- Failures include server timeouts and HTTP status codes as described in the following table:
  | Result | Description |
  | --- | --- |
  | **400** | Bad Requests that cannot be attributed to caller defects as defined by the protocols |
  | **500 Internal Server Error** | Server error |
  | **501 Not Implemented** | Operation not supported |
  | **50x** | Other server failure codes |

#### Sync Client API Reliability

The sync client must deliver a highly reliable integration with Microsoft Office applications before the end-to-end experience is generally available:

- 99.95% reliable per API

See [Sync client integration overview](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/about) for information about the sync client APIs for Windows and macOS.

## Performance

#### Host API Performance

Microsoft and each CSPP Plus host will measure the performance of the host at the WOPI API layer. The host must deliver acceptable performance on a select subset of performance-critical APIs:

##### Fixed Size APIs

Achieve less than 1.5 second response times at 95th percentile, as measured from the client \(including network latency\) for the following APIs:

- [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table)
- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [GetCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock)

##### Chunk Size APIs

Achieve less than 2 second completion times at the following 95th percentile performance, as measured from the client \(including network latency\) for the following APIs:

- [GetChunkedFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunked-file)
- [GetChunks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunks)

Note

Chunk size isn’t directly related to the overall file size and can't be controlled by the host or the client; the chunk sizes are based on the files' content. Assuming files from third-party hosts will look about the same as SharePoint/OneDrive files in aggregate, the 95th percentiles should be roughly the same.

#### Sync Client API Performance

Sync client performance has to be effectively real-time \(no in-line network calls\) and so should be less than 10 ms at 95th percentile per API call.

## Scale

To get an accurate measure of quality, the reliability measure above will be reviewed for the trailing 10,000 data points per requirement.
