<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/b2b-government-national-clouds -->
<!-- Sitemap-Last-Modified: 2025-07-07 -->

# Microsoft Entra B2B in government and national clouds

Microsoft Azure [national clouds](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-national-cloud) are physically isolated instances of Azure. B2B collaboration isn't enabled by default across national cloud boundaries, but you can use Microsoft cloud settings to establish mutual B2B collaboration between the following Microsoft Azure clouds:

- Microsoft Azure global cloud and Microsoft Azure Government
- Microsoft Azure global cloud and Microsoft Azure operated by 21Vianet

Organizations with multiple tenants across Microsoft clouds can use [cross-cloud synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview) to automate creating, updating, and deleting B2B users.

## B2B collaboration across Microsoft clouds

To set up B2B collaboration between tenants in different clouds, both tenants need to configure their Microsoft cloud settings to enable collaboration with the other cloud. Then each tenant must configure inbound and outbound cross-tenant access with the tenant in the other cloud. For details, see [Microsoft cloud settings](https://learn.microsoft.com/en-us/entra/external-id/cross-cloud-settings).

## B2B collaboration within the Microsoft Azure Government cloud

Within the Azure US Government cloud, B2B collaboration is enabled between tenants where:

- Both tenants are within Azure US Government cloud, *and*
- Both tenants support B2B collaboration.

Azure US Government tenants that support B2B collaboration can also collaborate with social users using:

- Microsoft accounts
- Google accounts
- Email one-time passcode accounts

If you invite a user outside of these groups \(for example, if the user is in a tenant that isn't part of the Azure US Government cloud or doesn't yet support B2B collaboration\), the invitation fails or the user can't redeem the invitation.

For Microsoft accounts, there are known limitations with accessing the Microsoft Entra admin center:

- Newly invited MSA guests are unable to redeem direct link invitations to the Microsoft Entra admin center
- Existing MSA guests are unable to sign in to the Microsoft Entra admin center.

For details about other limitations, see [Microsoft Entra ID P1 and P2 Variations](https://learn.microsoft.com/en-us/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

### How can I tell if B2B collaboration is available in my Azure US Government tenant?

To find out if your Azure US Government cloud tenant supports B2B collaboration, take the following steps:

1. In a browser, go to the following URL, substituting your tenant name for *<tenantname>*:

   `https://login.microsoftonline.com/<tenantname>/v2.0/.well-known/openid-configuration`
2. Find `"tenant_region_scope"` in the JSON response:

   - If `"tenant_region_scope":"USGOV”` appears, B2B is supported.
   - If `"tenant_region_scope":"USG"` appears, B2B isn't supported.

## B2B collaboration in Microsoft Azure operated by 21Vianet

Microsoft Azure operated by 21Vianet supports the following identity providers for B2B collaboration:

- Microsoft Entra ID
- SAML/WS-Fed

For more information about Microsoft Azure operated by 21Vianet, see [Service availability and roadmaps](https://learn.microsoft.com/en-us/azure/china/concepts-service-availability).

## Next steps

See the following articles on Microsoft Entra B2B collaboration:

- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [Delegate B2B collaboration invitations](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure)
