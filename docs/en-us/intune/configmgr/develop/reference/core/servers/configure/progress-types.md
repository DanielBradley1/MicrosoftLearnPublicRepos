<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/progress-types -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Progress Types

Progress states for a download.

Note

For a non-status change \(for example, if there was just transfer of bytes\), specify NULL for progress type.

## Syntax

```
//  Progress types:
//******************************************************************************
static const WCHAR S_DTS_PROGRESS_DOWNLOADING_MANIFEST[]    = L"DownloadingManifest";
static const WCHAR S_DTS_PROGRESS_PROCESSING_MANIFEST[]     = L"ProcessingManifest";
static const WCHAR S_DTS_PROGRESS_CREATING_DIRECTORIES[]    = L"CreatingDirectories";
static const WCHAR S_DTS_PROGRESS_PREPARING_DOWNLOAD[]      = L"PreparingDownload";
static const WCHAR S_DTS_PROGRESS_DOWNLOADING_DATA[]        = L"DownloadingData";
```

## Types

| Progress type | Description |
| --- | --- |
| S\_DTS\_PROGRESS\_DOWNLOADING\_MANIFEST | Determining list of files to download. |
| S\_DTS\_PROGRESS\_PROCESSING\_MANIFEST | Processing list of files. |
| S\_DTS\_PROGRESS\_CREATING\_DIRECTORIES | Creating subdirectories based on list of files. |
| S\_DTS\_PROGRESS\_PREPARING\_DOWNLOAD | Manifest processing complete, starting download. |
| S\_DTS\_PROGRESS\_DOWNLOADING\_DATA | Downloading files. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
