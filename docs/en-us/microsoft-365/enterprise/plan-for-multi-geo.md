<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-multi-geo?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# Plan for Microsoft 365 Multi-Geo

This guidance is for administrators of [*Tenants*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) preparing their Microsoft 365 *Tenant* to meet their [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) requirements.

In a [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) configuration, your Microsoft 365 *Tenant* consists of a [*Primary Provisioned Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) location and multiple [*Satellite Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) locations. You retain a single *Tenant* that spans across multiple [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) locations retaining single-tenant administration and full-fidelity collaboration experiences across *Geographies*.

To help you understand the basic concepts of *Multi-Geo* configuration, review [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

Enabling *Multi-Geo* requires four key steps:

1. Purchase the *Multi-Geo Capabilities in Microsoft 365* add-on SKU for your Microsoft 365 subscription.
2. Configure any workloads that require customer specific settings for *Multi-Geo*.
3. Set your users' [*Preferred Data Location \(PDL\)*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to the desired *Satellite Geography* location. A new user's OneDrive site, Exchange Online mailbox, and Teams chat store is provisioned in the *Geography* defined by their *PDL* value if the value is configured prior to assigning them a Microsoft 365 license. When an existing user's *PDL* value is set to a new value, then their existing Exchange Online mailbox and Teams chat store will automatically be migrated to the new *Geography*.
4. Migrate your users' existing OneDrive sites from the *Primary Provisioned Geography* location to their *Satellite Geography* data location as needed. OneDrive sites don't migrate automatically like Exchange Online mailboxes or Teams chat stores.

See [Configure Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-tenant-configuration?view=o365-worldwide) for details on each of these steps.

See the [Availability section](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide#microsoft-365-multi-geo-availability) of the Microsoft 365 *Multi-Geo* Overview page for the *Geographies* that can be a *Satellite Geography*.

## Best practices

We recommend that you create a test user in Microsoft 365 to do some initial testing. We'll walk through some testing and verification steps with this user before you proceed to onboard production users into Microsoft 365 *Multi-Geo*.

Once you've completed testing with the test user, select a pilot group - perhaps from your IT department - to be the first to use the *Multi-Geo* supporting workloads in *Satellite Geographies*.

Each user should have a *Preferred Data Location \(PDL\)* set so that Microsoft 365 can determine in which *Geography* location to provision or relocate their data to. The user's *Preferred Data Location* must match one of the available *Geographies*. While the *PDL* field isn't mandatory, we do recommend that a *PDL* value is set for all users. Users without a *PDL* value set will be provisioned in the *Primary Provisioned Geography*. If the *PDL* value isn't a valid value, then a user's data will be provisioned in the *Primary Provisioned Geography*.

Create a list of your users and include their user principal name \(UPN\) and the Preferred Data Location code. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

If your users are synchronized from an on-premises Active Directory system to Microsoft Entra ID, then you must set the *Preferred Data Location* as an Active Directory attribute and synchronize it by using Microsoft Entra Connect. You can't directly configure the *Preferred Data Location* for synchronized users using [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview). The steps to set up *PDL* in Active Directory and synchronize it are covered in [Microsoft Entra Connect Sync: Configure preferred data location for Microsoft 365 resources](https://learn.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

The administration of a *Multi-Geo* *Tenant* can differ from a non-*Multi-Geo* *Tenant* in some scenarios. For example, many SharePoint and OneDrive settings and services are *Multi-Geo* aware. We recommend that you review [Administering a multi-geo environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/administering-a-multi-geo-environment?view=o365-worldwide) before you proceed with your configuration.

Read [User experience in a multi-geo environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-user-experience?view=o365-worldwide) for details about your end users' experience in a *Multi-Geo* environment.

To get started configuring Microsoft 365 *Multi-Geo*, see [Configure Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-tenant-configuration?view=o365-worldwide).

Once you've completed the configuration, remember to [move users' OneDrive sites](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide#move-a-onedrive-site) as needed to get your users working from their preferred data locations.

## Related topics

[Microsoft 365 Multi-Geo eDiscovery configuration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-ediscovery-configuration?view=o365-worldwide)
