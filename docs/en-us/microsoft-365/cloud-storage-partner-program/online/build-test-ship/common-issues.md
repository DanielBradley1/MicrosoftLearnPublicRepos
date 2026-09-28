<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/common-issues -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Common implementation problems

The following are the most common Microsoft 365 for the web implementation issues.

### When an Microsoft 365 for the web application loads, it immediately displays a *Session expired* error

This is typically caused by supplying an invalid [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) value. Despite its misleading name, it does *not* represent a duration of time for which the access token is valid. For more information, see [the documentation on access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property).

### The Microsoft 365 for the web applications don't load in the correct mode; as in, they load in view mode instead of edit mode

The most common cause of this behavior is that the [action URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls) for the application is not being generated properly. Check that your action URLs match the templates provided in the **urlsrc** property in [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery). Common mistakes include removing required parameters from the query string or not properly removing and filling in [Placeholder values](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#placeholder-values).

### After editing a document in Microsoft 365 for the web, opening the same document in view mode doesn’t contain the changes

The Microsoft 365 for the web applications utilize a [cache](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/security#office-for-the-web-viewing-cache), so the most likely reason for seeing stale content in view mode is because you haven't properly updated the [Version](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#version) value you return in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

If you're providing a [SHA256](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#sha256) value, ensure that this value is also recalculated properly when the file content changes.

### When co-authoring in Microsoft 365 for the web, all users have the name *Guest*

Microsoft 365 for the web applications use the [UserFriendlyName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userfriendlyname) if provided, so check that you're providing that value in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
