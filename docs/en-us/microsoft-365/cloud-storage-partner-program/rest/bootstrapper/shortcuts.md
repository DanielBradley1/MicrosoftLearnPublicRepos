<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# Shortcut operations

![iOS](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-ios-only.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The following operations are defined on the Bootstrapper endpoint in addition to the Ecosystem endpoint. They are provided on the Bootstrapper endpoint as shortcuts to reduce HTTP round trips for native applications that use the Bootstrapper. They are equivalent to calling [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap), then using the [EcosystemUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#ecosystemurl) to immediately execute an operation on the Ecosystem endpoint.

For example, in order to get the root container, a WOPI client might execute the following operations:

1. Call [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap).
2. Using the [EcosystemUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap#ecosystemurl) from the [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) response, call the [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer) operation.

However, using the [GetRootContainer \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer#getrootcontainer-bootstrapper) shortcut operation, the WOPI client can skip calling [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap), and instead get the root container directly using an OAuth 2.0 token.

Important

Implementing shortcut operations is optional. If a host does not implement them, they should simply respond to the request as though it is a standard [**Bootstrap**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) request. In other words, a host that doesn’t implement shortcut operations can simply ignore the **X-WOPI-EcosystemOperation** header and treat the request as a standard [**Bootstrap**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) request.

WOPI clients must thus expect that some shortcut operations will not include the data expected, and should fall back to calling the appropriate operation on the Ecosystem endpoint in such cases.

With this in mind, the responses for each ‘shortcut’ operation are a combination of the [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) response and the response for the corresponding operation on the Ecosystem endpoint. The Bootstrapper response is contained in the `Bootstrap` property, and the operation’s response is contained in a separate property with a name specific to the operation.

For example, the response to the [GetRootContainer \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer#getrootcontainer-bootstrapper) shortcut operation looks like this:

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=<ecosystem_token>",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  },
  "RootContainerInfo": {
    "ContainerPointer" : {
      "Url" : "http://.../wopi*/containers/<containerId>?access_token=<per_container_token>",
      "Name" : "Container Name"
    },
    "ContainerInfo" : {
      "Name" : "Container Name",
      "HostUrl" : "http://contoso/324332",
      "SharingUrl" : "http://contoso/323432/efewos",
      "UserCanCreateChildContainer" : false,
      "UserCanCreateChildFile" : false,
      "UserCanDelete" : false,
      "UserCanRename" : false
    }
  }
}
```

Note that since these operations are exposed through the Bootstrapper endpoint, they will be called using OAuth 2.0 access tokens, not WOPI access tokens.

- [🚧 GetFileWopiSrc \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getfilewopisrc)
- [GetRootContainer \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer)
