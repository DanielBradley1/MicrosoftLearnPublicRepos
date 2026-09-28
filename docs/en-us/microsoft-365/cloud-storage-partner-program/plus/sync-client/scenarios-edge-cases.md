<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/scenarios-edge-cases -->
<!-- Sitemap-Last-Modified: 2022-09-08 -->

# Scenarios and edge cases

Learn how sync-client integration works in key scenarios and edge cases.

## Open in-sync third-party synced file via File Explorer for the first time \(Windows\)

| User actions | Product behavior |
| :--- | :--- |
| 1. In File Explorer or the Common File Dialog \(CFD\), double-clicks the third-party synced file.<br>2. Edits or coauthors the file.<br>3. Closes the file. | 1. Office uses the local path to the local file to open and display contents without requiring a network zero round trip *if the file supports coauthoring*. Otherwise, the file opens from the local file \(no coauthoring\).<br>2. The local path is converted to a service URL via registry and COM calls. The hash of the local content is verified to match the hash from the sync client.<br>3. Edits are uploaded to and downloaded from the service.<br>4. The third-party sync client keeps the local file in sync.<br>5. When the file is closed, it's deleted from the Office cache. |

## Open in-sync third-party synced file via the macOS Finder for the first time \(macOS\)

| User actions | Product behavior |
| :--- | :--- |
| 1. In the Finder, double-clicks the third-party synced file.<br>2. Edits or coauthors the file.<br>3. Closes the file. | 1. The third-party sync client is expected to set its sync domain with the OS so that a call to `NSURLIsUbiquitousItemKey` succeeds.<br>2. The XPC service converts the local path to a service URL after the service verifies that the local hash matches the hash from the sync client.<br>3. Office uses the local path and the local file to open and display the file contents without requiring a network round trip *if the file supports coauthoring*. Otherwise, the file opens from the local file \(no coauthoring\).<br>4. Edits are uploaded to and downloaded from the service.<br>5. The third-party sync client keeps the local file in sync.<br>6. When the file is closed, it's deleted from the Office cache. |

## Open third-party synced file while offline

In this scenario, while a user is offline, the user opens a third-party synced file in Microsoft Office by double-clicking the file in File Explorer or the macOS Finder.

| User actions | Product behavior |
| :--- | :--- |
| 1. Edits the file, then saves it.<br>2. Closes Office. | 1. The third-party sync client is expected to respond, even when the user is offline.<br>2. Office identifies the file as a third-party synced file via registry values. Then, it gets properties from the sync client via COM/XPC. *If the properties returned by the host in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp#supportscoauth)indicate that the file doesn't support coauthoring \(the `SupportsCoauth` property is `false`\), Office opens the file as a local file \(with no coauthoring\)*.<br>3. The file is in sync based on the `FileChecksum` property and the hash on disk.<br>4. Office opens with coauthoring support without requiring a network round trip.<br>5. Edits remain in the upload branch pending upload. Edits aren't persisted to the file on disk. While the user is offline, edits remain only in the Office cache.<br>6. *Pending Upload* is shown in the title bar throughout the session.<br>7. When the file is closed, the file remains in the Office cache because of the pending uploads.<br>8. When the file is closed, a final modal prompt tells the user that contents aren't yet uploaded. |

## Open file with pending changes in Office file cache from previous session

| User actions | Product behavior |
| :--- | :--- |
| 1. Completes the *Open third-party synced file while offline* scenario.<br>2. In File Explorer or the macOS Finder, double-clicks to open Office with a pending upload from the previous offline session file.<br>3. Edits the file, and then saves it.<br>4. Closes Office. | 1. *If the file doesn't support coauthoring, the file is opened as a local file and pending changes aren't uploaded.*<br>2. If the file does support coauthoring, Office loads the contents from the Office cache.<br>3. The contents from the local file in the synced folder are not used by Office, and they are not displayed to the user.<br>4. The contents in the Office cache, including pending edits, are loaded and displayed to the user.<br>5. Edits are uploaded to the service, along with edits from the previous session left in the cache.<br>6. If uploads are successful, the file is deleted from the Office cache when the file is closed. |

## Open out-of-sync third-party synced file via File Explorer or macOS Finder

In this scenario, while a user is offline, the user edits a local third-party synced file via OpenOffice.

| User actions | Product behavior |
| :--- | :--- |
| 1. Closes OpenOffice.<br>2. In File Explorer or the macOS Finder, double-clicks the file to open the same file with Office.<br>3. Closes Office. | 1. Office identifies the file as a third-party synced file via registry values, and then gets the file properties from the sync client via COM/XPC. *If the properties returned by the host in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp#supportscoauth) indicate that the file doesn't support coauthoring \(the `SupportsCoauth` property is `false`\), Office opens the file as a local file \(with no coauthoring\).*<br>2. The `FileChecksum` value that's retrieved from the sync client doesn't match the hash of the file on disk, which indicates that the local file isn't synced.<br>3. Office opens the file as local-only with no coauthoring support.<br>4. No entry is made for this file in the Office cache.<br>5. The sync client maintains the local file in sync. |

## Open third-party synced file via path from the MRU list

In this scenario, the local path is stored in the most recently used \(MRU\) list from the previous sync-backed file open \(the most common case\).

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens the file from the MRU list.<br>2. Edits the file.<br>3. Closes the file. | 1. The local path is mapped with help from the sync engine to the WOPI URL.<br>2. Office opens the file without requiring a network round trip \(including Excel\) from the local disk, with coauthoring support. *If the file properties returned by the host in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp#supportscoauth) indicate that the file doesn't support coauthoring \(the `SupportsCoauth` property is `false`\), Office opens the file as a local file \(with no coauthoring\).*<br>3. If everything is in sync, the file is deleted from the Office cache when the file is closed. |

## Open third-party synced file via URL from the MRU list

In this scenario, the service URL is stored from the previous URL open.

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens the file from the MRU list.<br>2. Edits the file.<br>3. Closes the file. | 1. The URL isn't mapped to the local path. The local sync client isn't involved at all.<br>2. Office doesn't open the file without a network round trip to download content. Because it's a first open, Office downloads the entire file prior to opening it.<br>3. The file is opened with coauthoring support and edits are uploaded to the service. *If the properties returned by the host in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp#supportscoauth) indicate that the file doesn't support coauthoring \(the `SupportsCoauth` property is `false`\), Office won't open the file*.<br>4. The file remains in the Office file cache because it was opened via a URL. |

## Open third-party synced file via File Explorer or the macOS Finder when the sync client doesn't respond

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens Task Manager and stops the third-party sync client process.<br>2. Double-clicks the file or CFD to open the Office file in the synced folder.<br>3. Closes Office. | 1. When the file is opened, Office detects via registry values or the `NSURLIsUbiquitousItemKey` API that the path belongs to a third-party sync client.<br>2. Office attempts to cocreate the COM object to communicate with the sync client by using the `IStorageProvider` APIs or an XPC equivalent.<br>3. Any failure that occurs while attempting to use `CoCreate`, `GetPropertyHandlerFromPath`, `RetrieveProperties`, or XPC equivalents from the sync client results in a local-only open without coauthoring support\*. Includes scenarios in which:<br><br>   - The COM call times out.<br>   - The sync client isn't running.<br>   - The sync client failed to respond with all required properties.<br><br><br>     <br>   <sup>\*</sup>If the sync client becomes responsive mid-session, nothing changes after the file is opened. Office writes only to the local file on disk without coauthoring support. |

## Save As to a third-party service offline

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens an existing local file on the desktop.<br>2. Saves as via **Save A Copy** > **Browse** > **CFD** > **C:\\users\\syncclient**.<br>3. Enters a file name.<br>4. Selects **Save**.<br>5. Closes the file. | 1. Office doesn't find an existing file in the synced folder.<br>2. Office doesn't attempt to communicate with the sync client.<br>3. Office creates the file in the local synced folder.<br>4. Office opens the file as local-only without coauthoring support.<br>5. After the sync client is in sync, a subsequent open has coauthoring support. |

## Save As to a third-party synced folder via the macOS Finder or CFD

| User actions | Product behavior |
| :--- | :--- |
| 1. Drags a large file to a synced folder.<br>2. Before the sync client uploads the file, double-clicks the file.<br>3. Closes the file. | 1. Office detects that the file belongs to a sync root and attempts to get the file properties via COM or XPC.<br>2. The sync client is expected to fail `RetrieveProperties` or the XPC call with `NotFound` or an equivalent error.<br>3. Office opens the file as local-only without coauthoring support.<br>4. The sync client continues to sync the file to the service while the file is open and after it's closed. |

## Drag a file to a third-party synced folder and immediately open

| User actions | Product behavior |
| :--- | :--- |
| 1. Drags a large file to a synced folder.<br>2. Before the sync client uploads the file, double-clicks the file.<br>3. Closes the file. | 1. Office detects that the file belongs to a sync root and attempts to get the file properties via COM or XPC.<br>2. The sync client is expected to fail `RetrieveProperties` or the XPC call with `NotFound` or an equivalent error.<br>3. Office opens the file as local-only without coauthoring support.<br>4. The sync client continues to sync the file to the service while the file is open and after it's closed. |

## Open a file with more changes from the server

In this scenario, a third-party synced file is in sync locally, but pending changes on the service haven't yet been downloaded by the sync client.

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens the file.<br>2. Waits for changes to appear.<br>3. Closes the file. | 1. The hash that's retrieved from the sync client and the hash of the file on disk matches.<br>2. The file opens without requiring a network round trip and displays the contents on disk.<br>3. Office uses the contents on disk to ask the service for any deltas.<br>4. Server changes are downloaded and displayed to the user. The local file in the synced folder remains stale.<br>5. The sync client independently keeps the local file in sync.<br>6. When the file is closed, it's deleted from the Office cache. |

## Rename a file outside the app when the file is already in the Office cache with pending changes

| User actions | Product behavior |
| :--- | :--- |
| 1. Opens the file with third-party sync integration.<br>2. Closes the file \(leaving file in the Office cache\).<br>3. Renames the file via File Explorer or the macOS Finder and waits for the sync client to propagate changes to the service.<br>4. Double-clicks to open the file in File Explorer or the macOS Finder. | 1. Office detects that the file is in the sync folder and gets the usual metadata through COM/XPC.<br>2. `WOPIUrl` is critical because it indicates that the file exists on the service and allows the file to be mapped in the Office cache.\*<br>3. Office finds the existing row entry in its cache by using the `WopiSrc` value.<br>4. The local contents from the disk aren't shown to the user.<br>5. The contents in the cache are shown to the user and the file opens online with coauthoring support. |

## Open the locally synced file that's left after the sync client is uninstalled and remove fails

| User actions | Product behavior |
| :--- | :--- |
| 1. Stops syncing a root or uninstalls the sync client.<br>2. The sync client is expected to remove synced files from client, but if failure occurs or while uninstalling the file, some files might be left over.<br>3. Syncs the client folder and double-clicks the file in File Explorer to open the file. | Windows:<br><br>1. After Office fails to find the right handler in the registry, it opens the file as local-only.<br>2. If a failure leaves the registry entries in place, Office fails while cocreating the nonexistent process. The file is again opened as local-only without coauthoring support.<br><br>Mac:<br><br>- In macOS, failures in `NSURLIsUbiquitousItemKey` after the engine is uninstalled are expected. |

## Next steps

- Learn how Office gets [data](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/data) from third-party sync engines.
- Learn how Office gets [metadata](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/sync-client/metadata) from third-party sync engines.
