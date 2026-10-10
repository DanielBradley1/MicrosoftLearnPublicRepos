<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-choose-solution?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Choose the right Microsoft 365 Data Residency solution

This article helps you determine which Microsoft 365 [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) solution meets your organization's requirements. Before proceeding, review [Compare data residency offerings](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide) to understand the differences between each option.

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Step 1: Determine your *Tenant's* Default Geography

Your [*Tenant's*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) [*Default Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) determines which included *Data Residency* commitments are available and which paid add-ons are available to you.

To find your *Default Geography*:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.
3. Review the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to see your *Tenant's* current data locations.

## Step 2: Check eligibility for included commitments

Based on your *Default Geography*, you may already have *Data Residency* commitments at no additional cost. For a complete view of which commitment types \(Product Terms, [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions), [*ADR*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)\) are available per [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) and service, see [Data residency commitments by Geography](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide#microsoft-365-data-residency-commitments-by-geography).

### Product Terms

The [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) include *Data Residency* commitments if your *Default Geography* is:

- Australia, Brazil, Canada, France, Germany, India, Japan, Norway, Qatar, South Africa, South Korea, Sweden, Switzerland, United Arab Emirates, United Kingdom, United States, or European Union

Select commercial *Tenants* in France, Germany, Norway, Sweden, or Switzerland can configure whether the in-country commitment is active. Review the [data residency setting for commercial customers in select geographies](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms?view=o365-worldwide#data-residency-setting-for-commercial-customers-in-select-geographies) before deciding whether you need another offering.

### European Union Data Boundary \(EUDB\)

You automatically receive [*EUDB*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitments if:

- Your sign-up location is in a country or region in the EU or EFTA, **and**
- You don't have a *Multi-Geo* subscription \(this also includes *Tenants* that previously had *Multi-Geo* but haven't yet completed deprovisioning\)

Important

*EUDB* and *Multi-Geo* are mutually exclusive. If your *Tenant* has or previously had a *Multi-Geo* subscription that hasn't been fully deprovisioned, it is not in scope for *EUDB*, even if the *Tenant* is in a country or region in the EU or EFTA.

## Step 3: Assess your requirements

Use the following questions to determine if you need additional *Data Residency* capabilities beyond the included commitments.

### Do you need expanded service coverage?

If you require *Data Residency* commitments for services beyond Exchange Online, SharePoint, OneDrive, Microsoft Teams, and Microsoft 365 Copilot, consider:

- **EUDB**: If you're in a country or region in the EU or EFTA and are eligible, *EUDB* covers expanded services including Microsoft Defender for Office P1, Exchange Online Protection, Office for the web, Viva Connections, and Microsoft Purview.
- ***ADR***: If you're in an eligible [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions), *ADR* provides commitments for expanded services within your specific country or region.

### Do you need to store data in multiple locations?

If your organization has users in multiple countries or regions with different *Data Residency* requirements:

- ***Multi-Geo*** is the only option that enables storing [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) across multiple *Geographies* within a single *Tenant*.

### Do you need data in a specific Local Region Geography?

If regulations or policies require data to remain within a specific country or region \(not just a broader region like the EU\):

- ***ADR*** provides commitments for *Local Region Geographies* with expanded service coverage.
- ***Multi-Geo*** allows you to specify the *Geography* for each user's data.

## Step 4: Select your solution

Use this decision matrix to identify the right solution for your organization.

### Table 1.4: Decision matrix

| Your situation | Recommended solution |
| :--- | :--- |
| *Default Geography* is in an eligible location and you only need coverage for core services | Review the *Data Location Card*. [*Product Terms*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitments are included, but select commercial *Tenants* must ensure the in-country setting matches their requirements. |
| Sign-up location is in EU/EFTA, you don't have *Multi-Geo*, and EU/EFTA data storage meets your needs | No action needed—*EUDB* commitments apply automatically |
| You need expanded service coverage in an eligible *Local Region Geography* | Purchase *Advanced Data Residency* |
| You need to store different users' data in different *Geographies* | Purchase *Multi-Geo Capabilities* |
| Your *Default Geography* isn't eligible for an included commitment and you need a [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) | Evaluate *ADR* or *Multi-Geo* based on your *Tenant's* *Default Geography* eligibility |

## Step 5: Verify and implement

Before implementing, review [How customer data can move between Geographies](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide#how-customer-data-can-move-between-geographies) to understand what data movement to expect under each commitment type—including the implications of having no commitment.

After determining your solution:

1. **For included commitments** \(*Product Terms* or *EUDB*\): Verify your eligibility and configuration using the *Data Location Card* in the Microsoft 365 admin center.
2. **For *ADR***:

   - Confirm your *Tenant's* *Default Geography* is in an eligible *Local Region Geography*
   - Purchase *ADR* licenses for 100% of paid seats
   - Opt-in to data migration if needed
   - See [Advanced Data Residency](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide) for details

3. **For *Multi-Geo***:

   - Purchase *Multi-Geo* licenses for at least 5% of eligible users
   - Configure [*Satellite Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) and set [*Preferred Data Locations*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for users
   - See [Multi-Geo Capabilities overview and requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide) for details

## Next steps

- [Product Terms Data Residency](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms?view=o365-worldwide)
- [EU Data Boundary for the Microsoft Cloud](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn)
- [Advanced Data Residency](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide)
- [Multi-Geo Capabilities overview and requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)
- [Find your data location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide)
