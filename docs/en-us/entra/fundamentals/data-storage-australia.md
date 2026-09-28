<!-- Source: https://learn.microsoft.com/en-us/entra/fundamentals/data-storage-australia -->
<!-- Sitemap-Last-Modified: 2026-03-16 -->

# Identity data storage for Australian and New Zealand customers in Microsoft Entra ID

## Overview

Microsoft Entra ID stores identity data in a location chosen based on the address provided by your organization when subscribing to a Microsoft service like Microsoft 365 or Azure. For information on where your Identity Customer Data is stored, review the Microsoft Trust Center section titled [Where is your data located?](https://www.microsoft.com/trustcenter/privacy/where-your-data-is-located).

Note

Services and applications that integrate with Microsoft Entra ID have access to Identity Customer Data. Evaluate each service and application you use. Determine how that specific service and application process identity data, and whether they meet your company's data storage requirements.

For customers who provided an address in Australia or New Zealand, Microsoft Entra ID keeps identity data for these services within Australian datacenters:

- Microsoft Entra Directory Management
- Authentication

All other Microsoft Entra services store customer data in global datacenters.

## Microsoft Entra multifactor authentication

Multifactor authentication stores Identity Customer Data in global datacenters. To learn more about the user information collected and stored by cloud-based Microsoft Entra multifactor authentication and Azure multifactor authentication Server, see [Microsoft Entra multifactor authentication user data collection](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-data-residency).

## Next steps

For more information about multifactor authentication, see this article:

- [What is multifactor authentication?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks)
