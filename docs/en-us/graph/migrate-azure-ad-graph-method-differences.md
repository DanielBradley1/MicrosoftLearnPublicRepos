<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-method-differences -->
<!-- Sitemap-Last-Modified: 2025-02-21 -->

# Differences in actions between Azure AD Graph and Microsoft Graph

> This article is part of *Step 1: review API differences* in the [Azure AD Graph app migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) series.

Some Azure Active Directory \(Azure AD\) Graph actions have changed. If an action is **not** shown in this list, it's already available in the [v1.0 version](https://learn.microsoft.com/en-us/graph/api/overview) of Microsoft Graph, with exactly the same name as in Azure AD Graph.

| Azure AD Graph  <br>\(v1.6\) function or action | Microsoft Graph  <br>\(resource/method\) | Comments |
| --- | --- | --- |
| getAvailableExtensionProperties | beta - *Not available*  <br>v1.0 - [directoryObjects/getAvailableExtensionProperties](https://learn.microsoft.com/en-us/graph/api/directoryobject-getavailableextensionproperties) |  |
| getObjectsByObjectId | beta - [directoryObjects/getByIds](https://learn.microsoft.com/en-us/graph/api/directoryobject-getbyids?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [directoryObjects/getByIds](https://learn.microsoft.com/en-us/graph/api/directoryobject-getbyids) |  |
| invalidateAllRefreshTokens | beta - [revokeSignInSessions](https://learn.microsoft.com/en-us/graph/api/user-revokesigninsessions?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [revokeSignInSessions](https://learn.microsoft.com/en-us/graph/api/user-revokesigninsessions) |  |
| isMemberOf | beta - *Not planned*  <br>v1.0 - *Not planned* | Use [checkMemberGroups](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups) and [List memberOf](https://learn.microsoft.com/en-us/graph/api/group-list-memberof) instead. |
| restore | beta - [restore \(selected directory objects\)](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [restore selected directory objects\)](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore) | You can also view supported directory objects such as deleted applications, users, and groups and permanently delete them. |

## Next step

[Review the migration checklist again](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist)
