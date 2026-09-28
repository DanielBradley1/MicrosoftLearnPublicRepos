<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/saml-protocol-reference -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# How the Microsoft identity platform uses the SAML protocol

The Microsoft identity platform uses the SAML 2.0 and other protocols to enable applications to provide a single sign-on \(SSO\) experience to their users. The [SSO](https://learn.microsoft.com/en-us/entra/identity-platform/single-sign-on-saml-protocol) and [Single Sign-Out](https://learn.microsoft.com/en-us/entra/identity-platform/single-sign-out-saml-protocol) SAML profiles of Microsoft Entra ID explain how SAML assertions, protocols, and bindings are used in the identity provider service.

The SAML protocol requires the identity provider \(Microsoft identity platform\) and the service provider \(the application\) to exchange information about themselves.

When an application is registered with Microsoft Entra ID, the app developer registers federation-related information with Microsoft Entra ID. This information includes the **Redirect URI** and **Metadata URI** of the application.

The Microsoft identity platform uses the cloud service's **Metadata URI** to retrieve the signing key and the logout URI. This way the Microsoft identity platform can send the response to the correct URL. In the [Microsoft Entra admin center](https://entra.microsoft.com/);

- Open the app in **Microsoft Entra ID** and select **App registrations**
- Under **Manage**, select **Authentication**. From there you can update the Logout URL.

Microsoft Entra ID exposes tenant-specific and common \(tenant-independent\) SSO and single sign-out endpoints. These URLs represent addressable locations, and aren't only identifiers. You can then go to the endpoint to read the metadata.

- The tenant-specific endpoint is located at `https://login.microsoftonline.com/<TenantDomainName>/FederationMetadata/2007-06/FederationMetadata.xml`. The *<TenantDomainName>* placeholder represents a registered domain name or TenantID GUID of a Microsoft Entra tenant. For example, the federation metadata of the `contoso.com` tenant is at: `https://login.microsoftonline.com/contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`
- The tenant-independent endpoint is located at `https://login.microsoftonline.com/common/FederationMetadata/2007-06/FederationMetadata.xml`. In this endpoint address, *common* appears instead of a tenant domain name or ID.

## Next steps

For information about the federation metadata documents that Microsoft Entra ID publishes, see [Federation Metadata](https://learn.microsoft.com/en-us/entra/identity-platform/federation-metadata).
