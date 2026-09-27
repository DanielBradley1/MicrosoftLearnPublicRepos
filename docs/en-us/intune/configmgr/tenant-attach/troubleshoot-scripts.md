<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-scripts -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Troubleshoot Scripts for devices uploaded to the admin center

*Applies to: Configuration Manager \(current branch\)*

Use the following to troubleshoot Scripts in the Microsoft Intune admin center:

## Common issues

### You don’t have access to view this information

**Error message:** You don’t have access to view this information. Make sure a proper user role is assigned from Intune.

**Possible cause:** The user account needs an [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned. In some cases, this error may also occur during replication of information and it resolves without intervention after a few minutes.

### Configuration Manager doesn't meet the minimum version prerequisite

**Error message:** Configuration Manager doesn't meet the minimum version prerequisite.

**Possible causes:** Your Configuration Manager sites are not running a supported version of Configuration Manager. Verify that every site in the hierarchy runs a supported version of Configuration Manager.

### Unable to get Scripts information

**Error message:** Unable to get Scripts information. Make sure Microsoft Entra ID and AD user discovery are configured and the user account accessing tenant attach features from the Microsoft Intune admin center is discovered by both. Verify that the user has proper permissions in Configuration Manager.

**Possible causes:** Typically, this error is caused by an issue with the admin account. Below are the most common issues with the administrative user account:

1. Use the same account to sign in to the admin center. The on-premises identity must be synchronized with and match the cloud identity.
2. Verify the account has **Read** permission for the device's **Collection** in Configuration Manager.
3. Verify the account has **Read Resource** permission for the device's **Collection** in Configuration Manager.
4. Make sure that Configuration Manager has discovered the administrative user account you're using to access the tenant attach features within Microsoft Intune admin center. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

   If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
5. Verify the discovery data. Select your user account. In the ribbon, on the **Home** tab select **Properties**. In the properties window, confirm the following discovery data:

   - **Microsoft Entra tenant ID**: This value should be a GUID for the Microsoft Entra tenant.
   - **Microsoft Entra user ID**: This value should be a GUID for this account in Microsoft Entra ID.
   - **User Principal Name**: The format of this value is user@domain. For example, `jqpublic@contoso.com`.


   If the Microsoft Entra properties are empty, check the configuration of the site's [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### Unable to get device information

**Error message:** Unable to get device information. Make sure Microsoft Entra ID and AD user discovery are configured and the user is discovered by both. Verify that the user has proper permissions in Configuration Manager.

**Possible cause:** Make sure that Configuration Manager has discovered the administrative user account you're using to access the tenant attach features within Microsoft Intune admin center. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

1. Verify the discovery data. Select your user account. In the ribbon, on the **Home** tab select **Properties**. In the properties window, confirm the following discovery data:

   - **Microsoft Entra tenant ID**: This value should be a GUID for the Microsoft Entra tenant.
   - **Microsoft Entra user ID**: This value should be a GUID for this account in Microsoft Entra ID.
   - **User Principal Name**: The format of this value is user@domain. For example, `jqpublic@contoso.com`.


   If the Microsoft Entra properties are empty, check the configuration of the site's [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### Unexpected error occurred

**Error message:** Unexpected error occurred

#### Possible cause

Verify the account has **Read Resource** permission for the device's **Collection** in Configuration Manager.

#### Error code 500 with an unexpected error occurred message

If you see `System.Security.SecurityException` in the **AdminService.log**, verify that your user principal name \(UPN\) discovered by [Active Directory User discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) isn't set to a cloud UPN rather than an on-premises UPN. An empty UPN value is also acceptable as it means the Active Directory discovered domain name is used. If you see cloud-only UPN \(example: onmicrosoft.com\) that's not valid domain UPN \(contoso.com\), you have an issue and may need to go [set the UPN suffix in Active Directory](https://learn.microsoft.com/en-us/office365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization#add-upn-suffixes-and-update-your-users-to-them).

#### Other possible causes of unexpected errors

Unexpected errors are typically caused by either [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point), [administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview), or connectivity issues.

1. Verify the service connection point has connectivity to the cloud using the **CMGatewayNotificationWorker.log**.
2. Verify the administrative service is healthy by reviewing the SMS\_REST\_PROVIDER component from site component monitoring on the central site.
3. IIS must be installed on provider machine. For more information, see [Prerequisites for the administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview#prerequisites).

## Known issues

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).
