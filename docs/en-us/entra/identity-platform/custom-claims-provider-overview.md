<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview -->
<!-- Sitemap-Last-Modified: 2025-09-16 -->

# Custom claims provider

This article provides an overview to the Microsoft Entra custom claims provider.

When a user authenticates to an application, a custom claims provider can be used to add claims into the token. A custom claims provider is made up of a custom authentication extension that calls an external REST API, to fetch claims from external systems. A custom claims provider can be assigned to one or many applications in your directory.

Key data about a user is often stored in systems external to Microsoft Entra ID. For example, secondary email, billing tier, or sensitive information. Some applications may rely on these attributes for the application to function as designed. For example, the application may block access to certain features based on a claim in the token.

The following video provides an excellent overview of the Microsoft Entra custom authentication extensions and custom claims providers:

<iframe src="https://www.youtube-nocookie.com/embed/ZU90avf0Qyc?si=Z8Z3gR9fzZFzb5Bq" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Use a custom claims provider for the following scenarios:

- **Migration of legacy systems** - You may have legacy identity systems such as Active Directory Federation Services \(AD FS\) or data stores \(such as LDAP directory\) that hold information about users. You'd like to migrate these applications, but can't fully migrate the identity data into Microsoft Entra ID. Your apps may depend on certain information on the token, and can't be rearchitected.
- **Integration with other data stores that can't be synced to the directory** - You may have third-party systems, or your own systems that store user data. Ideally this information could be consolidated, either through [synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync) or direct migration, in the Microsoft Entra directory. However, that isn't always feasible. The restriction may be because of data residency, regulations, or other requirements.

Note

A custom claims provider isn't the only way to add custom claims to a token. You can also [customize claims issued in the JSON web token \(JWT\) for enterprise applications](https://learn.microsoft.com/en-us/entra/identity-platform/jwt-claims-customization).

## Token issuance start event listener

An event listener is a procedure that waits for an event to occur. The custom authentication extension uses the **token issuance start** event listener. The event is triggered when a token is about to be issued to your application. When the event is triggered the custom authentication extension REST API is called to fetch attributes from external systems.

To set up a custom claims provider, you'll need to [create a REST API with a token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-setup), then [configure a custom claim provider for a token issuance event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration).

## Authentication events trigger for Azure Functions client library for .NET

The authentication events trigger for Azure Functions allows you to implement a custom extension to handle Microsoft Entra ID authentication events. The authentication events trigger handles all the backend processing for incoming HTTP requests for authentication events.

- Token validation for securing the API call
- Object model, typing and IDE intellisense
- Inbound and outbound validation of the API request and response schemas

## See also

- [Create a REST API with a token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-setup)
- [Custom claims provider reference](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-reference) article.
