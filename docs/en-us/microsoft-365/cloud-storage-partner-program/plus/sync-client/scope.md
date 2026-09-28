<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/scope -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Sync client integration scope

This article describes the scope of sync client integration.

## Out of scope

Note the following scope limitations for sync client integration:

- There's no support for iOS or Android.
- There's no Windows Runtime/Project Centennial app support.
- Open requests started from a service URL, including opens from a protocol handler or from a URL in the most recently used \(MRU\) list and backstage, are opened as server-only with coauthoring support. However, they don't benefit from opening and displaying contents based on the local file without requiring a network round trip using the sync-client integration described in this section.
- If a third-party sync engine isn't running, responding, installed, or signed in on Windows:

  - Coauthoring is disabled if files are opened from the local path. Files are opened as local-only.
  - If it's not turned on, the third-party sync engine might not attempt to start or sign in when we CoCreate a handle on `IStorageProviderHandler`. This situation will create additional delays in the open flow that will be perceived as "Office is slow to open."

- If there are dirty changes pending upload on the locally synced folder and the file is opened via the local path, Microsoft Office will open files as local-only without coauthoring support.
- When a file is closed, if there are no pending uploads, Office will delete the file entry in our internal local cache. This deletion allows support for opening and displaying contents based on the local file without requiring a network round trip for Excel files while preventing merge conflicts on future open operations. This is possible because the cache isn't kept in sync with the file when Office isn't running.
- If a file is a placeholder \(dehydrated\), the sync engine must download it before it starts Office if the file is being opened from the local path.
- Placeholder files that are opened while the user is offline will fail to open.

## Next steps

- Learn how Office gets [metadata](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/metadata) from third-party sync engines.
