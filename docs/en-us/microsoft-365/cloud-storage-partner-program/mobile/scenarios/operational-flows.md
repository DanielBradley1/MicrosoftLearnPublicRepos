<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/scenarios/operational-flows -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Operational flows for Microsoft 365 for mobile

This section outlines the implementation requirements and operational flows for user scenarios outlined in the [Browsing, opening, and saving files from Microsoft 365 for mobile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/scenarios/browse) section.

## Terminology

| Term | Definition |
| --- | --- |
| User | Self-explanatory |
| Office Client | The Microsoft 365 for mobile app, i.e. Word/Excel/PowerPoint |
| Office Identity Service | The Office Identity service is a service Microsoft 365 for mobile uses for handling user-identity information. In OAuth flows, the Office Identity Service behaves as the External User Agent |
| Bootstrapper URL | URL that the Storage Provider hosts to allow an Microsoft 365 Client app with a valid OAuth 2.0 access token to retrieve a WOPI access token |
| Token Endpoint URL | URL that the Storage Provider hosts and uses in order to generate access or refresh tokens |
| Services Manager | Microsoft 365-owned service that stores a Service Catalog, listing all of the available services for an app or endpoint |
| Storage provider | Refers to a CSPP partner who has integrated their service into Microsoft 365 for mobile |

Note

- Any time during these flows that Microsoft 365 for mobile tries to hit the bootstrapper and has expired or invalid OAuth credentials, Microsoft 365 for mobile will ask the user to log in again.
- Any time during these flows that Microsoft 365 for mobile has a missing, invalid, or expired WOPI access token, Microsoft 365 for mobile will attempt to get a valid WOPI access token by calling [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken).

## Add a Place

This describes the first time a user adds your storage provider using the `Add a Place` in Microsoft 365 for mobile. To correctly authenticate users, we use the following operational flow in order to connect a user’s storage provider account with their Microsoft 365 for mobile account.

![Image representation of the authentication flow for adding a place.](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/user-flows.png)

1. When the Microsoft 365 client boots, it calls the Services Manager for a list of available services. The Services Manager returns a Service Catalog, which is an alphabetically-sorted list of available providers and places to which the user can connect.
2. When the user clicks `Add a Place` in the Microsoft 365 for mobile backstage, they'll see your Storage Provider listed as an available place.
3. When the user adds the Storage Provider, the Microsoft 365 client makes an unauthenticated [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) call.
4. The [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) response includes the Authorization URI and token issue URI. Note that the Authorization URI must be provided as part of your [Onboarding information](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding) so we can add it as a trusted domain.
5. Microsoft 365 for mobile loads the Authorization URI in a web view, which prompts the user to sign in with the service provider. Once the user finishes the sign-in process, the web view reaches a redirect URI, which causes it to close. The redirect URI also provides an auth code to Microsoft 365 for mobile.
6. Microsoft 365 for mobile sends the auth code and token issue URI to the Office Identity Service.
7. The Office Identity Service sends the auth code and the client secret to the Token endpoint.
8. The Token Endpoint issues an access token and a refresh token \(if available\) back to the Office Identity Service.
9. The Office Identity Service makes an authenticated [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) call using the access token to retrieve the user's profile information.
10. The Office Identity Service sends the access and refresh tokens and the user's profile information to Microsoft 365 for mobile.
11. The user has now added the Storage Provider as a place. For the operational flow on browsing, opening, and saving files, see the next sections.

## Browse and open files

Here is the operational flow for browsing and opening files:

1. *Get the Root Container URL:* Microsoft 365 for mobile calls [GetRootContainer \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer#getrootcontainer-bootstrapper) to obtain a Root Container URL.
2. *Get the contents of the container:* Microsoft 365 for mobile calls [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren) on the Root Container. The results are a set of containers and files in the root container. If the user wants to browse to another container within the current container, Microsoft 365 for mobile calls [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) on the other container to check permissions, then calls [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren) on that second container. This step is repeated as the user browses the container hierarchy until the user selects the file they want to open.
3. *Check file permissions:* Once the user selects a file, Microsoft 365 for mobile calls [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) on that file to verify that the user has permissions to the file.
4. *Check file lock:*

   - If the earlier [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) call returned `true` for [SupportsGetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsgetlock), Microsoft 365 for mobile calls [GetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getlock#getlock). If the [GetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getlock#getlock) response is a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) or includes an **X-WOPI-Lock** header, the file is locked, and Microsoft 365 for mobile does not continue opening it.
   - If the earlier [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) call returned `true` for [SupportsGetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsgetlock), Microsoft 365 for mobile sends a [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock) request with a known invalid lock ID. If the [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock) response is a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) with a lock ID in the **X-WOPI-Lock** response header, the file is locked and Microsoft 365 for mobile does not continue opening it.

5. *Take a lock on the file:* Microsoft 365 for mobile calls [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) on the file, passing a lock ID it wishes to use in the **X-WOPI-Lock** request header. If the [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) call returns a [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1), the file is locked. Microsoft 365 for mobile will use the same lock ID when making future [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) requests.
6. *Download the file:* Microsoft 365 for mobile makes a [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) request on the file.

## Save and close a file

1. *Save the file:* If the user has made changes to the file, Microsoft 365 for mobile will update the file’s contents by calling [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile). The [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) request will include the current WOPI lock ID that Microsoft 365 for mobile previously used to lock the file.
2. *Unlock the file:* Microsoft 365 for mobile will make an [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) request against to unlock the file. This [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) request will include the current WOPI lock ID that Microsoft 365 for mobile previously used to lock the file.
