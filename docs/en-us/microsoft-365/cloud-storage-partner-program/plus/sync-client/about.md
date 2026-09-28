<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/about -->
<!-- Sitemap-Last-Modified: 2022-08-18 -->

# Sync client integration overview

To open Microsoft Office files stored in a third-party sync provider while supporting coauthoring and to support opening and display contents based on the local file without requiring a network round trip to download content, Office needs additional metadata and content from the third-party sync engine. This section describes how Office can retrieve the information it needs to open the locally synced files from a third-party sync engine's Windows File Explorer or macOS Finder folder. It describes how Office can do so without requiring a server round trip, while also supporting coauthoring scenarios.

## How sync client integration works

Office needs to get the `WOPISrc` where the file is stored on the server. It also needs some other data about the file to determine how to open it and where to open it from. In the open-via-local-path flow, we'll use the contents of the file already downloaded by the sync engine so the contents of the file display quickly without a full file download. When successfully opened third-party files are edited, Office uploads edits directly to the Web Application Open Platform Interface \(WOPI\) service. The third-party sync client continues to keep the local file synced.

## Next steps

- Learn about [terms](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary) you'll need to know.
- Understand the [scope](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/scope) of sync client integration.
