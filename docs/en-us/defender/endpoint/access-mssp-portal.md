<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/access-mssp-portal -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Access the Microsoft Defender MSSP customer portal

## Access an MSSP customer tenant in Microsoft Defender XDR

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Note

The following steps show MSSPs how to find a customer tenant ID and access the tenant-specific Microsoft Defender XDR portal URL.

By default, MSSP customers access their Microsoft Defender XDR tenant through the following URL: `https://security.microsoft.com/`.

MSSPs however, will need to use a tenant-specific URL in the following format: `https://security.microsoft.com?tid=customer_tenant_id` to access the MSSP customer portal.

In general, MSSPs will need to be added to each of the MSSP customer's Microsoft Entra ID that they intend to manage.

Use the following steps to obtain the MSSP customer tenant ID and then use the tenant ID to access the tenant-specific URL:

1. As an MSSP, log in to Microsoft Entra ID with your credentials.
2. Switch directory to the MSSP customer's tenant.
3. Select **Microsoft Entra ID > Properties**. You'll find the tenant ID in the Tenant ID field.
4. Access the MSSP customer portal by replacing the `customer_tenant_id` value in the following URL: `https://security.microsoft.com/?tid=customer_tenant_id`.
5. Access a Unified View for MSSP \(Preview\) in `https://mto.security.microsoft.com/`

## Related content

For more information, see the following articles:

- [Grant MSSP access to the portal](https://learn.microsoft.com/en-us/defender-endpoint/grant-mssp-access)
- [Configure alert notifications](https://learn.microsoft.com/en-us/defender-endpoint/configure-mssp-notifications)
- [Fetch alerts from customer tenant](https://learn.microsoft.com/en-us/defender-endpoint/api/fetch-alerts-mssp)
