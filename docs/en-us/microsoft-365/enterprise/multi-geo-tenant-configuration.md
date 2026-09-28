<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-tenant-configuration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# Microsoft 365 Multi-Geo *Tenant* configuration

Before you configure your *Tenant* for Microsoft 365 Multi-Geo, be sure you have read [Plan for Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-multi-geo?view=o365-worldwide).

To follow the steps in this article, you need a list of the *Geography* locations that you want to enable as *Satellite Geography* locations, and the test users that you want to provision for those locations.

Not all Multi-Geo workloads require customer driven configuration.

## Configuring Exchange Online for Multi-Geo

There is no customer driven configuration required to prepare Exchange Online in a Multi-Geo enabled *Tenant*. A customer may use all Geographies with Exchange Online as soon as Multi-Geo has been enabled within Exchange Online for their *Tenant*.

## Configuring Microsoft Teams for Multi-Geo

There's no customer driven configuration required to prepare Microsoft Teams in a Multi-Geo enabled tenant. A customer may use all Geographies with Microsoft Teams as soon as Multi-Geo has been enabled within Microsoft Teams for their *Tenant*.

## Configuring SharePoint and OneDrive for Multi-Geo

If you want to store data in a particular Geography, then that Geography must be configured for SharePoint and OneDrive ahead of time.

Once Multi-Geo has been enabled for your *Tenant* in SharePoint and OneDrive, the **Geo Locations** tab becomes available in the SharePoint admin center. If you don't see the **Geo Locations** tab, then your *Tenant* hasn't yet finished being enabled for Multi-Geo.

Important

If you have changed your fallback .onmicrosoft.com domain in the past, you must ensure that you change it back to the domain matching the one used in your SharePoint URLs before proceeding. For example, if your earlier fallback domain was contoso.onmicrosoft.com, your SharePoint domain is contoso.sharepoint.com and your current fallback domain is fabrikam.onmicrosoft.com, make sure you change your fallback domain back to contoso.onmicrosoft.com before creating your first satellite geography.

To add each Satellite Geography location for SharePoint and OneDrive where you want to store data:

1. Open the SharePoint admin center. and go to **Geo locations**.
2. Select **Add location**.
3. Select the location that you want to add, and then select **Next**.
4. Type the domain that you want to use with the geo location, and then select **Add**.
5. Select **Close**.

Provisioning may take from a few hours up to 72 hours, depending on the size of your *Tenant*. Once provisioning of a *Satellite Geography* location has completed, you'll receive an email confirmation. When the new *Geography* location appears in blue on the map on the Geo locations tab in the OneDrive and SharePoint admin center, then you can proceed to set users' preferred data location to that *Geography* location.

Important

Your new *Satellite Geography* location will be set up with default settings. This will allow you to configure that *Satellite Geography* location as appropriate for your local compliance needs.
