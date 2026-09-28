<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/coauth -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Co-authoring using Microsoft 365 for the web

Important

Participants in the Microsoft 365 - Cloud Storage Partner Program must support document editing and multi-user co-authoring.

Microsoft 365 for the web supports multiple users editing a document at the same time. Co-authoring in Microsoft 365 for the web includes real-time content updates between all users editing the document, as well as presence information and real-time cursor tracking for each user.

There are no unique WOPI host requirements beyond those described in this documentation in order to support co-authoring. But the guidelines around file IDs and locks, as described in the [Key concepts](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#key-concepts-to-understand-for-wopi-integration) section, are important for enabling co-authoring.

## Benefits from co-authoring support

Editing documents requires that Microsoft 365 for the web take a [lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock) on the file to ensure that only Microsoft 365 for the web is writing to the file. In cases where co-authoring isn't supported, this causes two problems.

First, users are unable to make changes to the file while someone else is editing it. You avoid this problem when you support co-authoring. With co-authoring in Microsoft 365 for the web, users are never locked out of editing a document.

Second, while Microsoft 365 for the web makes every attempt to unlock files after users have finished editing documents, there are circumstances where this might not happen. If [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) isn't called successfully, the file stays locked until the lock times out. This means that a user can be locked out of editing a file even if they were the one who originally locked it. When co-authoring is supported, the fact that the file is locked isn't a problem. Microsoft 365 for the web allows a user to edit the document as if they're co-authoring with themselves.

So, in addition to the obvious benefits for multi-user editing that come with real-time co-authoring, co-authoring in Microsoft 365 for the web provides benefits for single-user editing as well.

## How co-authoring works in Microsoft 365 for the web

When multiple users edit a single document using Microsoft 365 for the web, the Microsoft 365 for the web service manages the document changes and any necessary merges internally.

When a user attempts to edit a document, Microsoft 365 for the web takes a lock using the [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) operation and the access token of the current user. When additional users then attempt to edit the same document, Microsoft 365 for the web will verify those users have permission to edit the document by calling [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) using each user’s access token. If the `CheckFileInfo` call succeeds and the user has permissions to edit, they'll join the editing session already in progress.

Users who are collaborating then see the document content update in real-time as other users edit. But Microsoft 365 for the web only calls [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) periodically with the updated document contents. There are three critical questions to consider in co-authoring sessions:

1. **Auto-save frequency**: How frequently does the application call [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)?
2. **PutFile access token**: Which user’s access token is used when [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) is called?
3. **Permissions check frequency**: How often does the application verify that a user still has appropriate permissions to edit the document?

Question 3 is important because [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) is called using a single user’s access token, so a WOPI host is only able to check permissions of the user whose access token being used. Hosts rely on Microsoft 365 for the web to periodically verify that users still have edit permissions.

The answers to these questions differ between the Microsoft 365 for the web applications. The following table summarizes the behavior for each application, and the following sections describe the behavior in more detail.

***Table 1*** - *Summary of co-authoring behavior for Microsoft 365 applications*

| Application | Auto-save frequency | PutFile access token | Permissions check frequency |
| --- | --- | --- | --- |
| Word | Every 30 seconds if document is updated. | The access token of the user who made the most recent change to the document. | At least every five minutes. |
| Excel | Every two minutes. | The access token of the user who joined the editing session most recently. | At least every 15 minutes. |
| PowerPoint | Every 60 seconds if document is updated. | The access token of the user who made the most recent change to the document. | At least every five minutes. |

### Word for the web co-authoring behavior

**Auto-save frequency**: Every 30 seconds if document is updated. In other words, if users are actively editing a document, [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) is called every 30 seconds. But if users stop editing for a period of time, Word for the web doesn't call [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) until document changes are made again.

**PutFile access token**: For each auto-save interval, Word for the web uses the access token of the user who made the most recent change to the document. In other words, if User A and B both make changes to the document within the same auto-save interval, but User B made the last change, Word for the web uses User B’s access token when calling [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile). The file has both users’ changes, but the PutFile request uses User B’s access token.

But if User A made a change in one auto-save interval, and User B made a change in another auto-save interval, Word for the web makes two PutFile requests, each using the access token of the user who made the change.

**Permissions check frequency**: Word for the web verifies that a user has permissions by calling `CheckFileInfo` at least every five minutes while the user is in an active session.

### Excel for the web co-authoring behavior

**Auto-save frequency**: Every two minutes.

**PutFile access token**: Excel for the web always uses the access token of the user who joined the editing session most recently. This user is called the *principal user*. If the principal user leaves the session, the last user who joined the session becomes the principal user. In other words, if User A starts editing, User A is the principal user. If User B then joins the session, User B becomes the principal user, and Excel for the web uses User B’s access token when calling [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile). The file has both users' changes, but the `PutFile` request uses User B’s access token. If User C then joins the session, User C becomes the principal user.

If User C then leaves the session, User B becomes the principal user, and User B’s access token is used when calling PutFile.

**Permissions check frequency**: Excel for the web verifies that a user has permissions by calling [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock) at least every 15 minutes while the user is in an active session.

### PowerPoint for the web co-authoring behavior

**Auto-save frequency**: Every 60 seconds if a document is updated. In other words, if users are actively editing a document, [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) is called every 60 seconds. But if users stop editing for a period of time, PowerPoint for the web won't call [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) until document changes are made again.

Note

During a single-user editing session, PowerPoint for the web only calls [**PutFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) every three minutes. During an active co-authoring session, that frequency is increased to every 60 seconds.

**PutFile access token**: For each auto-save interval, PowerPoint for the web uses the access token of the user who made the most recent change to the document. In other words, if User A and B both make changes to the document within the same auto-save interval, but User B made the last change, PowerPoint for the web uses User B’s access token when calling [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile). The file has both users’ changes, but the `PutFile` request uses User B’s access token.

But if User A made a change in one auto-save interval, and User B made a change in another auto-save interval, PowerPoint for the web makes two `PutFile` requests, each using the access token of the user who made the change.

**Permissions check frequency**: PowerPoint for the web verifies that a user has permissions by calling `CheckFileInfo` at least every five minutes while the user is in an active session.

## Scenarios

The following scenarios illustrate the behavior WOPI hosts can expect for each Microsoft 365 for the web application when users are co-authoring.

All scenarios described here assume the following baseline flow.

Note

The pattern of WOPI calls described in the following section isn't meant to be absolutely accurate. Microsoft 365 for the web might make additional WOPI calls beyond those described here. These scenarios are meant only to illustrate the key behavioral aspects of the Microsoft 365 for the web applications. These scenarios aren't an absolute transcript of WOPI traffic between Microsoft 365 for the web and a WOPI host.

### Scenario baseline

1. User A begins editing a document.
2. Microsoft 365 for the web calls [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) using User A’s access token to verify the user has edit permissions.
3. Microsoft 365 for the web calls [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) using User A’s access token.
4. User B tries to edit the same document.
5. Microsoft 365 for the web calls [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) using User B’s access token to verify the user has edit permissions.

### Key points

- Microsoft 365 for the web always verifies that each user has appropriate edit permissions by calling [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) using that user's access token before letting them join the edit session.
- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) is always called using the access token of the first user to start editing the document.
- If users leave the editing session while others are still editing, Microsoft 365 for the web calls other lock-related operations, such as [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) or [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock), using the access tokens of other users that are still editing.

### Scenario 1

1. User A continues editing the document.
2. User B makes no changes.

***Table 2*** - *Co-authoring scenario 1*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | User A, since User B isn't editing. |  |
| Excel for the web | User B |  |
| PowerPoint for the web | User A, since User B isn't editing. |  |

### Scenario 2

1. User A continues editing the document.
2. User B also edits the document.

***Table 3*** - *Co-authoring scenario 2*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. |  |
| Excel for the web | User B |  |
| PowerPoint for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. |  |

### Scenario 3

1. User A leaves the editing session by closing the Microsoft 365 for the web application or navigating away.
2. User B continues editing the document.
3. User C tries to edit the same document.
4. Microsoft 365 for the web calls [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) using User C’s access token to verify the user has edit permissions.

***Table 4*** - *Co-authoring scenario 3*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | Any access token can be used, depending on which user changed the document most recently during the auto-save interval. |  |
| Excel for the web | User C |  |
| PowerPoint for the web | Any access token can be used, depending on which user changed the document most recently during the auto-save interval. |  |

### Scenario 4

1. User A continues editing the document.
2. User B is in the session but isn't editing the document.
3. While the editing session is in progress, User B’s permissions to edit the document are removed.

***Table 5*** - *Co-authoring scenario 4*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | User A, since User B isn't editing. | After no more than five minutes, Word for the web calls `CheckFileInfo` with User B’s access token. That call indicates that User B no longer has edit permissions, so User B is removed from the editing session. User A can continue editing the document. |
| Excel for the web | User B | Once User B’s edit permission is removed, all `PutFile` requests for the session fail. In no more than three minutes after the first `PutFile` failure, all users, including User A, are removed from the editing session. |
| PowerPoint for the web | User A, since User B isn't editing. | After no more than five minutes, PowerPoint for the web calls `CheckFileInfo` with User B’s access token. That call indicates that User B no longer has edit permissions, so User B is removed from the editing session. User A can continue editing the document. |

### Scenario 5

1. User A continues editing the document.
2. User B also continues editing the document.
3. While the editing session is in progress, User B’s permissions to edit the document are removed.

***Table 6*** - *Co-authoring scenario 5*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. | If a `PutFile` request is made using User B’s access token, it fails, and all users, including User A, are removed from the editing session. If `PutFile` is never called with User B’s access token, after no more than five minutes, Word for the web calls `CheckFileInfo` with User B’s access token. That call indicates that User B no longer has edit permissions, so User B is removed from the editing session. User A can continue editing the document. |
| Excel for the web | User B | Same as scenario 4. |
| PowerPoint for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. | If a `PutFile` request is made using User B’s access token, it fails, and all users, including User A, are removed from the editing session. If `PutFile` is never called with User B’s access token, after no more than five minutes, PowerPoint for the web calls `CheckFileInfo` with User B’s access token. That call indicates that User B no longer has edit permissions, so User B is removed from the editing session. User A can continue editing the document. |

### Scenario 6

1. User A continues editing the document.
2. User B also continues editing the document.
3. While the editing session is in progress, User A’s permissions to edit the document are removed.

***Table 7*** - *Co-authoring scenario 6*

| Application | PutFile access token used | Additional notes |
| --- | --- | --- |
| Word for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. | If a `PutFile` request is made using User A’s access token, it fails, and all users, including User B, are removed from the editing session. If `PutFile` is never called with User A’s access token, after no more than five minutes, Word for the web calls `CheckFileInfo` with User A’s access token. That call indicates that User A no longer has edit permissions, so User A is removed from the editing session. User B can continue editing the document. |
| Excel for the web | User B | After no more than 15 minutes, Excel for the web calls `RefreshLock` with User A’s access token. That call fails since User A no longer has edit permissions. So User A is removed from the editing session. User B can continue editing the document. |
| PowerPoint for the web | Either access token can be used, depending on which user changed the document most recently during the auto-save interval. | If a `PutFile` request is made using User A’s access token, it fails, and all users, including User B, are removed from the editing session. If `PutFile` is never called with User A’s access token, after no more than five minutes, PowerPoint for the web calls `CheckFileInfo` with User A’s access token. That call indicates that User A no longer has edit permissions, so User A is removed from the editing session. User B can continue editing the document. |
