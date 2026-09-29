<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-cross-cloud -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Manage tenants in other Microsoft cloud environments

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Multitenant management in Microsoft Defender supports government cloud environments to view their tenants in other cloud environments through cross-cloud visibility. Security operations teams operating in government cloud environments can now manage their entire security operations, including tenants in other cloud environments, in a single pane of glass.

Cross-cloud visibility allows GCC High and DoD multitenant customers to view and manage tenants in Microsoft GCC and Commercial cloud environments.

## Prerequisites

Cross-cloud visibility is available to government customers who have the applicable [licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/usgov#licensing-requirements).

In addition, ensure that the **Trust multi-factor authentication from Microsoft Entra tenants** setting is properly configured to successfully access tenants in Microsoft Commercial cloud environments. To configure MFA, see [Change inbound trust settings for MFA and device claims](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-settings-b2b-collaboration#to-change-inbound-trust-settings-for-mfa-and-device-claims).

### Configure B2B collaboration settings

Follow these steps to configure B2B collaboration settings.

#### Configure home tenant settings

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Navigate to **Identity > External identities > Cross-tenant access settings**, then select **Cross-tenant access settings**.
3. Select **Add organization**. Enter the tenant ID of the organization you want to add, then select **Add**.

Note

By default, a B2B inherits the default settings of your tenant.

Configure the home tenant settings to the following:

1. For the organization you added, select **Inbound access**.
2. Set B2B collaboration to **Block** for Access and Users.
3. On the Application tab, set access to **Block** and Applies to **All applications**, then select **Save**.
4. Select **B2B direct connect**, set access status to **Block** and Applies to **all users**.
5. On the Application tab, set access to **Block** and Applies to **All applications**, then select **Save**.

No other MFA trust settings are required for the home tenant \(the tenant from which you manage cross-cloud access\).

Configure outbound access settings for the home tenant by following these steps:

1. In the **Cross-tenant access settings** pane, select **Outbound access**.
2. Configure B2B collaboration by setting access status to **Allow**.
3. In the Applies to, select any depending on your requirements.
4. Select **External applications** and set access status to **Allow**.
5. Set the Applies to to **All external applications**. Select **Save**.
6. Select **B2B direct connect** and set access status to **Block**.
7. In the Applies to, select **All users**.
8. Select **External applications** and set access status to **Block**.
9. Set the Applies to to **All external applications**. Select **Save**.

#### Configure target tenant settings

Perform the following steps to add the target tenant organization:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Navigate to **Identity > External identities > Cross-tenant access settings**, then select **Cross-tenant access settings**.
3. Select **Add organization**. Enter the tenant ID of the organization you want to add, then select **Add**.

Configure the target tenant settings to the following:

1. For the organization you added, select **Inbound access**.
2. Set B2B collaboration to **Allow** for Access and Users.
3. On the Application tab, set access to **Allow** and Applies to **All applications**, then select **Save**.
4. Select **B2B direct connect**, set access status to **Block** and Applies to **All users**.
5. On the Application tab, set access to **Block** and Applies to **All applications**, then select **Save**.
6. Select **Trust settings**, then select **Trust multi-factor authentication from Microsoft Entra tenants**.

Configure outbound access settings for the target tenant by following these steps:

1. In the **Cross-tenant access settings** pane, select **Outbound access**.
2. Configure B2B collaboration by setting access status to **Block**.
3. In the Applies to, select **All users**.
4. Select **External applications** and set access status to **Block**.
5. Set the Applies to to **All external applications**. Select **Save**.
6. Select **B2B direct connect** and set access status to **Block**.
7. In the Applies to, select **All users**.
8. Select **External applications** and set access status to **Block**.
9. Set the Applies to to **All external applications**. Select **Save**.

## Manage tenants across cloud environments

### Add tenants from another cloud

To manage tenants from other Microsoft cloud environments:

1. Go to the [Multitenant management settings page](https://mto.security.microsoft.com/settings) in Microsoft Defender.
2. Select the dropdown beside **Add tenants**, then select **add from another cloud**.

   [![Screenshot of the Settings page with the Add tenant option highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-cross-cloud/mto-add-from-cloud-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-cross-cloud/mto-add-from-cloud.png#lightbox)
3. In the **Add from another cloud** pane, type the tenant ID or domain of the tenant you want to add, then select **Verify tenant**. The verification process looks at the added tenant’s information and permissions.

   [![Screenshot of the add tenants pane with the verification highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-cross-cloud/mto-verify-tenant-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-cross-cloud/mto-verify-tenant.png#lightbox)
4. Once verified, select **Add tenant** to complete the process.

The tenants list now includes the tenants from the external cloud environment you added. You can now manage these tenants as you would any other tenant in Microsoft Defender.

If you get an error during the verification process, you can:

- Check the tenant ID or domain you entered.
- Ensure you have the correct permissions to access the tenant.

To remove tenants from the list, select the tenant, then select **Remove tenants**.

After successfully adding tenants from other clouds, you can view the added cross-cloud tenants in other multitenant pages like the incidents and device inventory pages.

Note

When a cross-cloud tenant is added to a distribution profile and subsequently removed from cross-cloud visibility, the tenant's name is removed from the tenant list and won’t be available for content management. This is a recognized limitation of cross-cloud visibility and is currently under review. See [Content assignment failure in cross-cloud tenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-troubleshoot#content-assignment-failure-in-cross-cloud-tenant-management) for more information.

## Related content

- [View and manage incidents and alerts in multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-incidents-alerts)
- [Device inventory in multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-tenant-devices#device-inventory)
