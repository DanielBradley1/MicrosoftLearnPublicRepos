<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/editing-finished -->
<!-- Sitemap-Last-Modified: 2021-08-30 -->

# How does a WOPI host know when an editing session is finished?

While editing a file, a WOPI client will always maintain a WOPI lock on the file. When editing is complete, the file will be unlocked using the [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) WOPI operation. Thus, once the file is successfully unlocked, the editing session is completed.

WOPI clients will always call [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) at the end of an editing session, unless something happens that prevents the session from closing cleanly, such as a browser crash or a network dropout. In those cases the WOPI lock eventually times out, which is fundamentally equivalent to an explicit Unlock request.

Note

In [**co-authoring**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/coauth) sessions, the [**Unlock**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) operation will only be called when the last user editing the document ends their session. Thus, if hosts wish to track what users are editing a document, they cannot rely completely on the locked state of the document. Hosts can use the `Edit_Notification` message to help gauge activity within a co-authoring session.
