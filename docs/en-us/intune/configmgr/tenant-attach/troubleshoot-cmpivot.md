<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-cmpivot -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Troubleshoot CMPivot for devices uploaded to the admin center

*Applies to: Configuration Manager \(current branch\)*

Use the following to troubleshoot CMPivot in the Microsoft Intune admin center:

## Common issues

### You don’t have access to view this information

**Error message:** You don’t have access to view this information. Make sure a proper user role is assigned from Intune.

**Possible cause:** The user account needs an [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned. In some cases, this error may also occur during replication of information and it resolves without intervention after a few minutes.

### Unable to get device information

**Error message 1:** Unable to get device information. Make sure Microsoft Entra ID and AD user discovery are configured and the user is discovered by both. Verify that the user has proper permissions in Configuration Manager.

**Possible causes:** Typically, this error is caused by an issue with the admin account. Below are the most common issues with the administrative user account:

1. Use the same account to sign in to the admin center. The on-premises identity must be synchronized with and match the cloud identity.
2. Verify the account has **Read** permission for the device's **Collection** in Configuration Manager.
3. Make sure that Configuration Manager has discovered the administrative user account you're using to access the tenant attach features within Microsoft Intune admin center. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

   If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
4. Verify the discovery data. Select your user account. In the ribbon, on the **Home** tab select **Properties**. In the properties window, confirm the following discovery data:

   - **Microsoft Entra tenant ID**: This value should be a GUID for the Microsoft Entra tenant.
   - **Microsoft Entra user ID**: This value should be a GUID for this account in Microsoft Entra ID.
   - **User Principal Name**: The format of this value is user@domain. For example, `jqpublic@contoso.com`.


   If the Microsoft Entra properties are empty, check the configuration of the site's [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### Not authorized to view query results

**Error message:** Not authorized to view query results. Verify that you've been given permissions for CMPivot in Configuration Manager

**Possible causes:** Verify the user account has permissions for CMPivot. For more information see [Permissions for CMPivot](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/cmpivot-start#permissions).

#### Other possible causes of unexpected errors

Unexpected errors are typically caused by either [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point), [administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview), or connectivity issues.

1. Verify the service connection point has connectivity to the cloud using the **CMGatewayNotificationWorker.log**.
2. Verify the administrative service is healthy by reviewing the SMS\_REST\_PROVIDER component from site component monitoring on the central site.
3. IIS must be installed on provider machine. For more information, see [Prerequisites for the administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview#prerequisites).

## Known issues

### When the SMS provider is remote from the CAS, you may encounter an internal server error from the admin console

**Error message:** On-prem error code: 500 internal server error

**Possible scenario:** If the CAS has been upgraded to a new version but the primary site hasn't been upgraded yet, then the requests will be routed through the CAS provider. If the provider is remote, you may encounter an internal server error from the admin console.

**Workaround:** Follow the instructions for the [CAS has a remote provider](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot-changes#cas-has-a-remote-provider) scenario in the CMPivot article to work around this "double hop" scenario.

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).

## Next steps

[Troubleshoot tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot)
