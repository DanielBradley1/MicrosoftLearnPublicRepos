<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/testing -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# Test Microsoft 365 for the web integration

Before starting the [Launch process](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping), do the following testing on your integration.

## WOPI Validator tests

The automated tests in the following categories must be passing in the WOPI validator:

- HostFrameIntegration \(ValidLanguagePlaceholderValues might be skipped if the host isn't using the [UI\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#ui_llcc) or [DC\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#dc_llcc) placeholder values\)
- BaseWopiViewing
- CheckFileInfoSchema
- EditFlows
- Locks
- PutRelativeFile **or** PutRelativeFileUnsupported
- ProofKeys
- RenameFileIfCreateChildFileIsNotSupported **or** RenameFileIfCreateChildFileIsSupported \(applicable only if the host supports [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile)\)
- FileVersion
- PutUserInfo \(applicable only if the host supports [PutUserInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putuserinfo#putuserinfo)\)

Important

*All* of the applicable tests listed above *must* pass in order to go to production. We don't make exceptions to this requirement.

Tip

Hosts aren't required to support [**RenameFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile) or [**PutRelativeFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile). However, hosts that support these operations, or use application features that rely on them, must pass.

For example, [**binary file conversion**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion) requires the [**PutRelativeFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) operation be implemented, so hosts that support conversion must also pass the PutRelativeFile tests.

## Microsoft 365 for the web feature verification

Important

Your WOPI solution must support Word, Excel, and PowerPoint - even if the end user will not see all three applications in the user interface. All three applications must pass all applicable tests before your WOPI solution can be put into production.

Many Microsoft 365 for the web features rely on a host’s WOPI implementation. You should test the following features to help ensure your WOPI implementation is correct and that the Microsoft 365 for the web integration is well-executed.

### Co-authoring

Co-authoring support is a major boon to users, but it's also used to verify your implementation of file IDs and lock-related WOPI operations. **For this reason, multi-user co-authoring must be testable using the test accounts provided.**

Important

The Microsoft 365 for the web applications have unique behavior with respect to co-authoring. So, it's critical to test co-authoring in all three applications.

To check that co-authoring behaves as expected, you’ll need at least two different user accounts. Then, follow these steps:

1. As User A, share a document with User B.
2. Open the document in edit mode as User A.
3. Open that same document in edit mode as User B.
4. Check that both instances of the Microsoft 365 for the web application are participating in the co-authoring session.
5. Make edits to the document as both users and ensure that both instances of the application remain connected to the co-authoring session.
6. After making some edits, leave the session and verify that the saved file contains the edits made by both User A and User B.

#### Common issues

1. If the users remain in different sessions \(as in, co-authoring doesn't occur\), it likely means your WOPI file IDs aren't consistent. See [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) for more information.
2. If one of the users is *kicked out* of the session while editing, it likely means that you’re rejecting lock-related requests that come from a different user than the one who originally took the lock. WOPI locks aren't user-owned. For more information, see [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock).

### Single-user co-authoring

While the typical co-authoring scenario is two or more users collaborating on a single document in real-time, the feature also provides other benefits as outlined in [Benefits from co-authoring support](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/coauth#benefits-from-co-authoring-support).

To check that single-user co-authoring behaves as expected:

1. Open a document in edit mode.
2. Open a document in edit mode using the same user account originally used, but in a different browser.
3. Check that both instances of the Microsoft 365 for the web application are participating in the co-authoring session.

### Downloaded files should have most recent document changes

If you are providing a [DownloadUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl), you should ensure that a file downloaded using the Microsoft 365 for the web **Download a Copy** buttons contain the most recent edits. To test this:

1. Open a document in edit mode.
2. Make an edit to the document and wait for the *Saved to <HostName>* text to display.
3. Click the **File** > **Save As** > **Download a Copy** button.
4. Check that the downloaded file has the most recent edits you made to the document.

### Download a Copy should not re-direct

As describe in [DownloadUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl), Microsoft 365 for the web expects that when directing users to the DownloadUrl, the file is immediately downloaded. This URL should not direct the user to some separate UI to download the file.

### Rename

If you support renaming documents within Microsoft 365 for the web \(as in, [SupportsRename](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsrename) is `true`\), you should check that the rename operation behaves as expected. To test this:

1. Open a document in edit mode.
2. Click on the document name in the top title bar.
3. Rename the document.
4. Exit the Microsoft 365 for the web application and check that the file was renamed.

If you're displaying the document name in the browser window and tab using the HTML `title` tag, you should check that the document name is updated after the file is renamed. If it's not, check that you're properly handling the `File_Rename` PostMessage.

### Save As in Excel for the web

Excel for the web supports saving an open document as a new copy of that document using the **File** > **Save As** > **Save As** button. This feature uses the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) WOPI operation. You should test that this feature works as expected.

## UI integration

Ensure you follow the [UI guidelines](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/ui-guidelines) as well as the Microsoft Cloud Storage Partner Program Integration Terms.
