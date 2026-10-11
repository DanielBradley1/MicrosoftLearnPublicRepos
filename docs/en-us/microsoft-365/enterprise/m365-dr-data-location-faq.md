<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Data Location FAQ

This article answers frequently asked questions about finding where your Microsoft 365 [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is stored.

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Data Location Card

### Can I get exact details about where my data is stored?

Yes. Microsoft publishes datacenter locations at the city level for each [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions). Exact street addresses aren't disclosed for security reasons. This detail isn't shown on the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) due to space constraints.

For the complete list, see [Microsoft 365 datacenter locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-datacenter-locations?view=o365-worldwide).

**How to interpret the information:**

- **[*Local Region Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)** \(such as "France" or "Japan"\): Your data is stored within that country or region, in one or more of the cities listed.
- **[*Macro Region Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)** \(such as "Americas" or "European Union/EFTA"\): Your data is stored within that region, in one or more of the datacenter locations listed. Where applicable, the table identifies both the country or region and city.

Microsoft commits to storing your data within the country or region shown on your *Data Location Card*. However, due to operational needs like load balancing and capacity management, Microsoft doesn't guarantee a specific city within that *Geography*.

### Where is backup and disaster recovery data stored? Does replication cross borders?

For [*Tenants*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) with a [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions), Microsoft's commitments apply to all data stored at rest within the committed *Geography*, including replicated copies used for backup and disaster recovery.

- ***Local Region Geographies***: Backup and DR data remains within the committed country or region. For example, if your [*Committed Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is "France," replicated data stays within France.
- ***Macro Region Geographies***: Backup and DR data remains within the committed region, which may include multiple countries or regions. For example, "European Union/EFTA" includes datacenters across multiple countries or regions in the EU or EFTA.

For *Tenants* without a *Durable Commitment on Data Location*, Microsoft may replicate data across datacenters as needed to ensure service availability.

### What happened to the Legacy Move Program?

Microsoft discontinued the [*Legacy Move Program*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) on April 30, 2023. Customers who submitted requests before this deadline will be migrated under the original program terms.

[*ADR*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is now the only *Durable Commitment on Data Location* that includes migration services. To migrate your data to a *Local Region Geography*:

- **Enterprise Agreement or EES customers**: Work with your Microsoft account team to obtain *ADR* or *ADR-E* \(Education\) licenses.
- **Cloud Solution Provider \(CSP\) customers**: Work with your CSP partner to purchase *ADR*.

After purchasing, opt-in to migration through the *Data Location Card*. For details, see [ADR overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide).

### Are services like Microsoft Loop, Clipchamp, and voice/face enrollment covered by *ADR* or *Multi-Geo*?

These services aren't included in *Advanced Data Residency \(ADR\)* or [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitments as [*Microsoft 365 Core Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) or [*Microsoft 365 Expanded Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).

For information on where these services store data, see:

- [Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-services-data-location?view=o365-worldwide)
- [Non-Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-other-services-data-location?view=o365-worldwide)

### How do I find where my data is stored?

Use the *Data Location Card* in the Microsoft 365 admin center:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) as a Global Administrator.
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.

The *Data Location Card* displays the [*Current Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(where data is currently stored\) and *Committed Geography* \(where Microsoft commits to store data\) for each service.

For detailed instructions, see [Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide).

### Where can I learn more about Data Location Card scenarios?

For detailed walkthroughs of common scenarios—including mismatches between *Current Geography* and *Committed Geography*, services without a displayed location, *Multi-Geo* customer experiences, and tenants without an [*EUDB*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitment—see [Data Location Card common scenarios](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide#common-scenarios).

### Where will my data be provisioned?

Where your data is provisioned depends on two factors: your *Tenant's* [*Default Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) and the *Geographies* where the specific service is deployed. The following examples illustrate how these factors combine:

- **Example 1 — Service available in your country or region:** A *Commercial Tenant* with a *Default Geography* of "France" subscribes to Exchange Online, SharePoint, OneDrive, and Microsoft Teams. *Customer Data* is provisioned into the French *Local Region Geography*, because those services are deployed into French datacenters and the *Tenant's* *Default Geography* is France.
- **Example 2 — No local datacenter, but service is available in your broader region:** A *Commercial Tenant* with a *Default Geography* of "Belgium" subscribes to the same services. *Customer Data* is provisioned into *Macro Region Geography 4 — European Union/EFTA*, because there are no Microsoft 365 datacenters in Belgium and the closest compliant *Geography* is EU/EFTA. Belgian *Tenants* are eligible to reside within the [European Union Data Boundary \(EUDB\)](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn).
- **Example 3 — Service has limited deployment:** A *Commercial Tenant* with a *Default Geography* of "Japan" subscribes to Microsoft Forms. *Customer Data* is provisioned into *Macro Region Geography 3 — Americas*, because Forms is only deployed in the Americas and EU/EFTA \(EU/EFTA *Tenants* only\).
- **Example 4a — New subscription, service recently expanded:** A *Commercial Tenant* with a *Default Geography* of "Sweden" creates a new subscription that includes Microsoft Viva Engage. *Customer Data* is provisioned into *Macro Region Geography 4 — European Union/EFTA*, because Viva Engage is now deployed in EU/EFTA and Swedish *Tenants* are best served from that *Geography*.
- **Example 4b — Existing subscription before service expansion:** A *Commercial Tenant* with a *Default Geography* of "Sweden" subscribed to Viva Engage before it was deployed to EU/EFTA. *Customer Data* remains in *Macro Region Geography 3 — Americas*, because at the time of provisioning, Viva Engage only had a single deployment for all customers in the Americas.

For background on provisioning concepts, see [What is Microsoft 365 Data Residency?](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-what-is-data-residency?view=o365-worldwide). To find your current data location, see [Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide).

## Microsoft 365 Copilot data location

### Where does Microsoft 365 Copilot store my data?

The content of interactions with Microsoft 365 Copilot \(your prompts and Copilot's responses, including citations\) is stored at rest in the relevant *Local Region Geography* based on your *Tenant's* [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) configuration.

For *Multi-Geo* customers, Copilot uses the [*Preferred Data Location \(PDL\)*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for users to determine where to store interaction content. If *PDL* isn't set or is invalid, data is stored in the [*Tenant's Primary Provisioned Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).

For detailed information, see [Data Residency for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot?view=o365-worldwide).

### Is Microsoft 365 Copilot covered by ADR?

Yes. Microsoft 365 Copilot and Copilot Chat are included in *Advanced Data Residency \(ADR\)* commitments. The content of interactions is stored at rest in your *Local Region Geography* when you have a valid *ADR* subscription.

Required conditions:

1. *Tenant* has a sign-up country/region in a *Local Region Geography*
2. *Tenant* has valid *ADR* subscription for all users
3. *Tenant* Global Administrator has opted in to migration \(if data isn't already in the *Local Region Geography*\)

See [ADR commitments for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide#microsoft-365-copilot-and-microsoft-365-copilot-chat) for specific committed data.

### Is Microsoft 365 Copilot covered by *Multi-Geo*?

Yes. *Multi-Geo* capabilities in Microsoft 365 Copilot enable content of interactions to be stored at rest in a specified *Macro Region Geography* or *Local Region Geography* based on the user's *Preferred Data Location \(PDL\)*.

Required conditions:

1. *Tenant* has valid *Multi-Geo* subscription covering users in [*Satellite Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)
2. Active Enterprise or CSP Partner Agreement
3. Total purchased *Multi-Geo* units must be greater than 5% of eligible licenses

Note

*EUDB* and *Multi-Geo* are mutually exclusive. *Tenants* with *Multi-Geo* subscriptions are not in scope for *EUDB*, even if the *Tenant* is in a country or region in the EU or EFTA. For details, see [Compare eligibility and licensing](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide#compare-microsoft-365-eligibility-and-licensing).

### How does Copilot handle data when users collaborate across regions?

When users in different regions collaborate using Copilot:

**Document collaboration example:**

- User A creates a document stored in France \(their OneDrive location\)
- User B in Canada asks Copilot to rewrite a paragraph
- User B's prompt and Copilot's response are stored in Canada \(User B's *PDL*\)
- The original document and any accepted changes remain in France

**Teams meeting example:**

- Meeting recording location is determined by the *PDL* of the user who starts recording, or the meeting organizer if automatic recording is enabled
- When users in different regions interact with Copilot in Teams, their prompts and responses are stored based on their individual *PDL*

### Is Microsoft 365 Copilot covered by Product Terms data residency?

Yes. *Tenants* with a sign-up country/region in Australia, Brazil, Canada, the European Union, France, Germany, India, Japan, Norway, Qatar, South Africa, South Korea, Sweden, Switzerland, the United Kingdom, the United Arab Emirates, or the United States are covered by [*Product Terms*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) *Data Residency* commitments for Microsoft 365 Copilot.

For current language, see the [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all).

## Workload-specific data locations

### Where does Microsoft Teams store data?

Microsoft Teams stores different types of data in different locations:

| Data type | Storage location |
| :--- | :--- |
| **Chat/channel messages and team structure** | Azure-powered chat service in the user's or group's *Geography* |
| **Images and media in chats** | Azure Media Service in the same location as the chat service |
| **Meeting recordings** | OneDrive of the user who initiates the recording |
| **Files shared in Teams** | SharePoint \(for channels\) or OneDrive \(for chats\) |
| **Voicemail, calendar, contacts** | Exchange Online |

For *Multi-Geo* customers, Teams uses the user's or group's *Preferred Data Location \(PDL\)* to determine where to store chat data.

See [Data Residency for Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide) for complete details.

### Where does Microsoft Forms store data?

Microsoft Forms data storage depends on your *Tenant's* location:

| *Tenant* location | Forms data storage |
| :--- | :--- |
| Countries or regions in the EU | Macro Region Geography 4 – European Union/EFTA |
| Australia \(new *Tenants* or those who haven't used Forms\) | Australia |
| All other *Tenants* | United States |

Note

Forms doesn't currently have *ADR* commitments.

### Where does Planner store data?

Planner data storage follows the [Static data location information](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-other?view=o365-worldwide#static-data-location-information-for-select-services) based on your *Tenant's Default Geography*.

Note

Premium plan data is stored in Dataverse. Assigned tasks are also stored in the same Azure location as basic plans, and attachments are stored in the SharePoint location for the group. Planner doesn't currently participate in *ADR*. For more information, see [Security, privacy, and compliance in Microsoft Planner](https://learn.microsoft.com/en-us/planner/planner-security-privacy-compliance).

### Where does Whiteboard store data?

For information on Whiteboard data storage, see [Manage data for Microsoft Whiteboard](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-data-organizations).

### Where does Viva Engage store data?

For information on Viva Engage *Data Residency*, see [Data Residency - Viva Engage](https://learn.microsoft.com/en-us/viva/engage/manage-security-and-compliance/data-residency).

### Where does Viva Insights store data?

Viva Insights has different storage locations based on the feature:

| Feature | Data storage |
| :--- | :--- |
| **Personal insights** | Processed and stored in the employee's Exchange Online mailbox |
| **Advanced, Manager, and Leader insights** | See [Viva Insights data residency](https://learn.microsoft.com/en-us/viva/insights/advanced/setup-maint/data-residency) |

### Where does Viva Learning store data?

Viva Learning data storage follows the [Static data location information](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-other?view=o365-worldwide#static-data-location-information-for-select-services) based on your *Tenant's Default Geography*.

### Where does Viva Goals store data?

Viva Goals data storage:

| *Tenant* location | Data storage |
| :--- | :--- |
| *Tenants* in countries or regions in the EU Data Boundary or the UK \(created after December 5, 2022\) | EU data centers |
| All other *Tenants* | United States |

Note

Customers in EU/UK who signed up before December 5, 2022 have been migrated to EU data centers.

### Where does Viva Glint store data?

Viva Glint data region is determined by the *Default Geography* of the *Tenant* \(not individual users\):

| *Tenant* Default Geography | Data storage |
| :--- | :--- |
| US or EU/EFTA | US or EU/EFTA data centers \(matching *Tenant* location\) |
| Outside US or EU/EFTA | United States |

### Where does OneNote store data?

OneNote stores *Customer Data* in OneDrive. However, OneNote has an API that can cause persistent caches to be created outside of the *Geography* where OneDrive stores data.

### Where does Stream store data?

To find where Stream stores your data:

1. Open Microsoft Stream
2. Click the "?" \(help\) option
3. Click "About Microsoft Stream"

### Where is Intune data stored?

For Intune data storage locations, see [Data storage and processing in Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/privacy-data-store-process#storage-locations).

## Related resources

- [Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide)
- [Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-services-data-location?view=o365-worldwide)
- [Non-Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-other-services-data-location?view=o365-worldwide)
- [ADR overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide)
- [Multi-Geo overview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)
