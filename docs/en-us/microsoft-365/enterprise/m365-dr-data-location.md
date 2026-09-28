<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Learn More about The Data Location Card

This article is designed to help customers and Tenant Global Admins understand how they can determine where their in-scope customer data for Microsoft 365 services is currently stored at rest, and if their *Tenant* has a [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-1-definitions-and-terms).

Note

[Microsoft Defender for Office P1](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide), [Microsoft Purview \(select services\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide), and [Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide) are covered by [Durable Commitments on Data Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#durable-commitments-on-data-location) but are not currently displayed in the *Data Location Card*. Refer to [Where your Microsoft 365 customer data is stored](https://learn.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide) for more information.

## Locating Where your *Tenant's* Data is Stored at Rest

The *Data Location Card \(DLC\)* in the Microsoft 365 admin center allows Tenant Global Admins to see where in-scope customer data associated with certain *Microsoft 365 Core Services* and *Microsoft 365 Expanded Services* is stored at rest. To access the *Data Location Card*, select the **Data location** section in the Microsoft 365 admin center by navigating to **Admin** > **Settings** > **Org settings** > **Organization profile** > **Data location**.

## Overview of the Data at Rest Locations

The *Data Location Card* displays three columns outlining the covered *Services*, the *Current Geography*, and the *Committed Geography*.

The *Current Geography* refers to the location where the in-scope customer data is currently stored, while the *Committed Geography* refers to the location where Microsoft stores in-scope customer data based on the [data residency commitments applicable to the *Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#overview-of-data-residency).

## Finding The Commitments Applicable to a Microsoft 365 Service

Different Microsoft 365 services might be covered by different commitments depending on several factors, including the date of a customer's subscription, the date that a *Tenant* was provisioned, the *Default Geography* of a *Tenant*, and if *Product Terms* apply to certain Microsoft 365 services. The data location on the *DLC* displays the most conservative *Durable Commitment on Data Location*.

For simplicity, the *Data Location Card* only shows a single *Committed Geography* based on a customer's various commitments for their *Tenant*.

If a *Tenant*:

- Has an active *Advanced Data Residency \(ADR\)* subscription, then the *Committed Geography* reflects the *Local Region Geography* that is associated with the *ADR* commitment.
- Doesn't have *ADR* and qualifies for data residency based on [*Product Terms*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms-dr?view=o365-worldwide), the applicable *Geography* associated with the *Tenant's Product Terms* is listed.
- Doesn't have *ADR*, and doesn't qualify for data residency based on [*Product Terms*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms-dr?view=o365-worldwide), but the *Tenant's Default Geography* is in the *European Union* or *EFTA*, then the *Tenant's Committed Geography* is the *European Union/EFTA*.
- Doesn't meet any of the preceding conditions, in which case Microsoft stores the in-scope customer data where it best enables Microsoft to provide services to customers, and that data storage location is subject to change without notice. The *DLC* also displays "**No Commitment**" in the *Committed Geography* field.

## Product Terms Data Residency Setting

Important

*This setting is only available to eligible commercial Tenants with a Default Geography of France, Germany, Norway, Sweden, or Switzerland. Tenants with a paid data residency offering — Advanced Data Residency \(ADR\), Advanced Data Residency for Education \(ADR-E\), or Multi-Geo Capabilities — don't see this setting, because their data residency is already governed by that offering. Tenants that qualify for data residency based on Product Terms but didn't opt into the Legacy Move Program may not be eligible. If your organization isn't eligible, this setting doesn't appear and your current commitment is unchanged.*

Eligible *Tenants* can use the *Product Terms* data residency setting on the *Data Location Card* to choose whether Microsoft keeps their *Microsoft 365 Core Services* data at rest in their Product Terms-associated *Geography*, or allows that data to be stored and moved outside of it. The setting is located within the **Data location** section of the Microsoft 365 admin center. Navigate to **Admin** > **Settings** > **Org settings** > **Organization profile** > **Data location** > **Commitments**.

The setting applies only to the *Microsoft 365 Core Services*: Exchange Online, SharePoint, OneDrive for Business, Microsoft Teams, and Microsoft 365 Copilot and Microsoft 365 Copilot Chat.

Note

*This setting doesn't affect any European Union Data Boundary \(EUDB\) commitment. If your organization has an EUDB commitment, it remains in place regardless of how this setting is configured.*

| Setting | What it means |
| :--- | :--- |
| On | Microsoft keeps your *Microsoft 365 Core Services* data at rest in your Product Terms-associated *Geography*. |
| Off | Microsoft may store your *Microsoft 365 Core Services* data regionally within the *EU Data Boundary*. |

When you change this setting, your *Committed Geography* updates to reflect your choice. Because moving in-scope customer data takes time, your *Data Location Card* might temporarily show a mismatch between your *Current Geography* and *Committed Geography* until the move completes.

This choice isn't permanent. If the setting is Off, you can turn it back on at any time. Microsoft re-commits your data to your Product Terms-associated *Geography* and begins moving it back, which can take approximately 6 months to complete. For more information about the setting, see ["Overview of Product Terms Data Residency"](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms-dr?view=o365-worldwide).

## Understanding Mismatches Between *Current Geography* and *Committed Geography*

A discrepancy might appear between *Current Geography* and *Committed Geography* in certain circumstances, including the following scenarios:

1. ***ADR* Commitment Procured, Migration Not Yet Opted Into.** A customer has procured an *Advanced Data Residency \(ADR\)* commitment for their *Tenant*, and the Tenant Global Admin has not yet opted-in to migration. In this case, the *Data Location Card* shows a mismatch between *Committed Geography* and *Current Geography*. To rectify this discrepancy, the Tenant Global Admin must [opt-in to migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide#data-migration-management) and allow sufficient time for the migration to occur, as described in the next scenario.

   ![Screenshot of Data Location View Before Migration Opt-in.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-opt-in-0725.png?view=o365-worldwide)
2. ***ADR* Commitment Procured and Migration Opted Into** A customer has procured an *ADR* commitment on data location for their *Tenant* and has opted in to migration. While the *Tenant's Committed Geography* is updated to reflect the *Tenant's* new commitment, it [takes some time](https://go.microsoft.com/fwlink/p/?LinkId=523897) for the services to process the request and migrate in-scope customer data to the new location. The *Tenant's* *Data Location Card* continues to display a mismatch between *Current Geography* and *Committed Geography* until the data migration effort is complete.

   **Example**: A *Tenant's Data Location Card* displays a *Current Geography* of "**Asia Pacific**", but the customer recently purchased *ADR* for Indonesia for this *Tenant*. After opting-in to data migration, the *Tenant's Committed Geography* is updated to "**Indonesia**". However, the *Tenant's Current Geography* continues to display "**Asia Pacific**" until the in-scope customer data is migrated. When an individual service completes data migration efforts, the *Tenant's Data Location Card* is updated and displays a *Current Geography* of "**Indonesia**".

   ![Screenshot of Data Location View Migration in Progress.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-in-progress-0725.png?view=o365-worldwide)
3. ***Product Terms* Eligibility Without the *Legacy Move Program***. A customer's *Tenant* is eligible for data residency based on *Privacy and Security Product Terms*, but the customer didn't elect to take part in the *Legacy Move Program*. If the Tenant Global Admin didn't elect their *Tenant* to participate in the *Legacy Move Program* then the *Tenant's* *Data Location Card* may display a mismatch between the *Tenant's Current Geography* and *Committed Geography*.

   Data residency based on *Product Terms* doesn't include data migration into *Local Region Geographies*. *Tenants* remain eligible for a data residency commitment for in-scope customer data associated with *Microsoft 365 Core Services* in their respective *Local Region Geography*-once their in-scope customer data is migrated to that location. To initiate migration, customers must purchase the required number of *ADR* licenses and opt-in to the migration process.

   ![Screenshot of Data Location View For Customer Who Didn't Opt-in To Legacy Move Program.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-no-legacy-move-opt-in-0725.png?view=o365-worldwide)
4. ***ADR* [Licensing Requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide#licensing-requirements) Are Not Met**. If a *Tenant* was once covered by an *ADR* commitment, and fails to meet the [licensing requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide#licensing-requirements) - the *Tenant's Data Location Card* reflects this change in the *Committed Geography*.

   **Example**: If an Indonesian customer no longer meets the required number of *ADR* licenses needed to retain in-scope customer data in Indonesia, the *Tenant's Committed Geography* changes from "**Indonesia**" to "**No Commitment**" in their *Data Location Card*.

   ![Screenshot of Data Location View For Customer With Insufficient ADR Seat Coverage.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-insufficient-seat-coverage-0725.png?view=o365-worldwide)
5. **Local Region *Current Geography* With a Macro Region *Committed Geography***. A *Tenant's* *Current Geography* for the Microsoft 365 services displays a *Local Region Geography*, but its *Committed Geography* displays a *Macro Region Geography*. In this case, the *Tenant's* in-scope customer data is compliant with the *Tenant's* *Committed Geography*. Information about the *Tenant's* current data location \(that is, *Current Geography*\) is more granular, indicating a specific location or set of locations.

   **Example**: A French *Tenant* with a *Current Geography* of "**France**" and a *Committed Geography* of "**European Union/EFTA**". Since "**France**" is part of the *European Union*, in-scope customer data is also within the "**European Union/EFTA**". In this example, "**France**" is a more specific and detailed location of where in-scope customer data is stored.

   ![Screenshot of Data Location View For Customer With Macro Region Geography for Committed Geography.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-committed-geography-macro-region-0725.png?view=o365-worldwide)
6. **No Data Location Displayed Under *Committed Geography***: In this case, information about the *Tenant's Current Geography* is accurate, and the *Tenant* simply doesn't have any *Durable Commitment on Data Location*.

   **Example**: A *Tenant* with a *Default Geography* of Laos, that isn't currently eligible to purchase *ADR* or *Multi-Geo* and doesn't qualify for data residency based on *Product Terms* or *EUDB*, sees a *Current Geography* where their in-scope customer data is currently stored, and "**No Commitment**" in the *Committed Geography* field.

   ![Screenshot of Data Location View For Customer With No Durable Commitments On Data Location.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-not-eligible-for-durable-commitment-0725.png?view=o365-worldwide)
7. **A *Tenant* Changed Its Product Terms Data Residency Setting**: When an eligible *Tenant* turns the setting Off, its *Committed Geography* for the *Microsoft 365 Core Services* changes to "No Commitment" and Microsoft may begin moving the in-scope customer data out of the Product Terms-associated *Geography*. When a *Tenant* turns the setting back on, its *Committed Geography* updates to the Product Terms-associated *Geography* right away, while the *Current Geography* continues to show the data's present location until migration back completes. In both directions, the *Data Location Card* may display a mismatch between *Current Geography* and *Committed Geography* until the move completes.

## Microsoft 365 Services without a *Current Geography* or *Committed Geography*

If there's no data location shown \(indicated by a "-" next to a Microsoft 365 service\), a *Tenant* doesn't currently have an active subscription for this service. For example, a *Tenant* without a Microsoft 365 Copilot subscription sees no data location next to that service.

![Screenshot of Data Location View For Customer With No Microsoft 365 Copilot Subscription.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-no-m365-copilot-subscription-0725.png?view=o365-worldwide)

## Data Location Card and *Microsoft 365 Multi-Geo Capabilities*

If a customer has a *Microsoft 365 Multi-Geo Capabilities* data residency offering, then the *Data Location Card* experience reflects only the information related to the [*Tenant's* central location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide#multi-geo-architecture). This is because the *Microsoft 365 Multi-Geo Capabilities* offering allows Tenant Global Admins to store data in multiple locations. Information on *Satellite Locations* isn't disclosed on the *Data Location Card*. For more information, please see the [*Microsoft 365 Multi-Geo* page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)

## Microsoft 365 Services stored in "Europe"

Certain *Tenants* might have their in-scope customer data stored in "**Europe**" but might not be provided with the *EUDB* commitment based on the *Tenant's Default Geography*. In these scenarios, users see a *Current Geography* of "**Europe**" and an information message stating "This tenant doesn't have an \[EU Data Boundary\] \(EUDB\) data residency commitment." at the bottom of the *DLC*. For more information on *EUDB* eligibility, see [How to configure services for use in the EU Data Boundary](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn#how-to-configure-services-for-use-in-the-eu-data-boundary). For more information on *EUDB* commitments, see the [Microsoft EU Data Boundary documentation](https://www.microsoft.com/trust-center/privacy/european-data-boundary-eudb?msockid=17b6c7f9a50068231a1fd4dea4ba694a) in the Microsoft Trust Center.

![Screenshot of Data Location View For Customer With No EUDB Commitment.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-no-eudb-commitment-0725.png?view=o365-worldwide)
