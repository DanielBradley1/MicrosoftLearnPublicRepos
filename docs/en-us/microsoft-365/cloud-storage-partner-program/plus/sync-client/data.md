<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/data -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# How Office gets data from third-party sync engines

In addition to metadata about a file, Microsoft Office also needs the contents of the local file. The data populates the Office file cache with the local copy of the file. The local copy allows users to immediately start reading and editing the file. No full-file downloads or round trips are needed in the critical open path. However, offline open operations in the same integrated mode are supported.

## How data is populated

Placeholder files must be hydrated by the sync engine at this point. The attempt to read the contents of the file should be the latest opportunity for the sync engine to hydrate it. No other calls from Office should be needed to hydrate a placeholder. A read attempt should be enough.

While resolving a local file as connected with a cloud file URL, after a file is determined to be a third-party synced file, Office will use the stream on disk to populate the Office file cache. It will then display file content to the user for read and edit. At this point, Office will also issue an async request to retrieve changes from the service, if there are any.

After the file is open, Office doesn't interact with the file-only disk or with the third-party sync client. Local user edits are uploaded to the service directly. They aren't written to the file on disk. The sync engine is expected to keep the file on disk in sync. Remote user edits during coauthoring also aren't persisted to the local file on disk.

After a successful open operation backed by sync-client integration, the local path used is stored in our MRU. This stored path allows future open operations of the same file via MRU to open sync-backed and without requiring a network round trip.

When a file is closed, the cache entry and file contents are generally deleted. There's an exception when the user has been working offline and there are changes in the cache that haven't been uploaded. This exception prevents the existence of stale data that's unsynced in our cache. Excel can have trouble merging data that's kept stale for a long time. For follow-up open operations for which there's already an entry for a given file in our cache, the branches aren't replaced with the local copy. Instead, the cached copy is opened and displayed to the user after MapPaths. This scenario implies that the previous session didn't save changes to the server, so we can't override it with local content.

## Next steps

- Learn how Office gets [metadata](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/metadata) from third-party sync engines.
- Learn how sync-client integration works in key [scenarios and edge cases](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/scenarios-edge-cases).
