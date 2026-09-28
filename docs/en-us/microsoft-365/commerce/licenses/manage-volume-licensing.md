<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/manage-volume-licensing?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Manage volume licensing agreements

Depending on the Microsoft volume licensing \(VL\) agreement program type you have, you can manage your VL agreements on different dedicated web sites.

This article addresses licensing management functions for legacy \(classic\) VL offers that were previously managed in the now-retired Volume licensing Service Center \(VLSC\).

## Before you begin

You must have a VL role to access VL agreements. These roles are assigned either during the VL agreement contract creation process or when a VL Administrator adds other VL users.

## Classic volume licensing

If you're a Commercial or Government Community Cloud customer, you can access the following VL agreement types in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339):

- Microsoft Enterprise and Enterprise Subscription
- Select and Select Plus
- Academic Agreements - Education Enrolment or School Enrolment
- Open Value, Open Value Subscription, and legacy Open License\* programs

\*The Open License program retired January 1, 2022. Users who registered their Open licenses with Microsoft before that date continue to have online access to them.

US Government customers must use specific versions of the admin center.

- Government Community Cloud High VL Administrators must use [https://portal.office365.us/adminportal/home](https://portal.office365.us/adminportal/home).
- Department of Defense VL Administrators must use [https://portal.apps.mil/adminportal/home](https://portal.apps.mil/adminportal/home).

## Changes to volume licensing roles and sign in requirements

We're making changes to VL roles and sign-in requirements for the Microsoft 365 admin center. For all new VL contracts, only the Notices and Online Admin Contact \(NTC\) and the Online Services Manager \(OSM\)\* automatically get access to VL pages in the Microsoft 365 admin center.

- The NTC must sign in and become the first online administrator \(OLA\) for that contract.
- As OLA, they must assign and manage VL roles for all other users for that contract, although they can assign additional OLAs.
- When adding VL users, OLAs no longer need to provide a user's business email and a separate Log in ID. Instead, VL roles must be assigned to a Microsoft Entra ID \(previously referred to as a Work or school account\).
- After a VL role is assigned, users can sign in directly without needing to select an invitation link and verify email address ownership.
- Newly added or edited VL users will receive an email notification confirming the permission change but can sign in without the notification.

\*If the VL contract didn't include a Microsoft Entra ID for the OSM, no role will be assigned in admin center. The OLA must assign a role after the appropriate Microsoft Entra ID has been determined.

This change will apply to the following agreement types:

- SPLA
- Select Plus
- Campus 3
- School 3
- ISV 3
- Open Value Subscription
- Open Value
- Select 6
- US Government

## VLSC functions moved to the Microsoft 365 admin center

The Volume Licensing Service Center \(VLSC\), where organizations previously managed licenses they purchased via the classic VL programs mentioned earlier in this article was retired in April 2024. VL functionality moved to the Microsoft 365 admin center, or to the equivalent admin centers for US government cloud users. VL Administrators who previously accessed VLSC with a Microsoft Entra ID automatically have access to the VL pages in the Microsoft 365 admin center.

All VLSC roles are enabled in the Microsoft 365 admin center with the same permissions, except for the Online Subscription Manager \(OSM\) role, which now has permission to manage online reservations.

## Other Microsoft licensing programs

The Microsoft licensing offers listed in this section are managed separately from classic VL offers on the VL pages of the Microsoft 365 admin center and aren't covered by articles in the **Manage volume licensing** section of the [Microsoft business subscriptions and billing documentation](https://learn.microsoft.com/en-us/microsoft-365/commerce/?view=o365-worldwide) site.

### Microsoft Products and Services Agreement

Licenses purchased via the Microsoft Product Services Agreement \(MPSA\) are registered and managed in the [Microsoft Business Center](https://businessaccount.microsoft.com/customer).

If you see an **MPSA products** tab in the admin center on the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page, those licenses are administered separately from the VL contracts available on the **Volume licensing** tab.

For more information about administering MPSA Purchase Accounts, see [Business Center Training & Resources \| Microsoft Volume Licensing](https://www.microsoft.com/licensing/existing-customer/business-center-training-and-resources).

### Microsoft Customer Agreement for Enterprise

Licenses purchased under a Microsoft Customer Agreement for Enterprise \(MCA-E\) are invoiced and administered separately from licenses displayed in the VL pages of the admin center. For more information, see [Set up billing for Microsoft Customer Agreement](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/mca-setup-account).

## Contact volume licensing support

Submit a case in the admin center > [Help & Support](https://go.microsoft.com/fwlink/p/?linkid=2166757). If you can't access the admin center, see [Contact volume licensing support](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/contact-vl-support?view=o365-worldwide).
