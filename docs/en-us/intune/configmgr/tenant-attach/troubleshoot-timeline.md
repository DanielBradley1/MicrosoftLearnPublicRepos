<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-timeline -->
<!-- Sitemap-Last-Modified: 2024-01-17 -->

# Troubleshoot the timeline for devices uploaded to the admin center

*Applies to: Configuration Manager \(current branch\)*

Use the following to troubleshoot the device timeline in the Microsoft Intune admin center:

## Common errors from the Microsoft Intune admin center

When viewing or synching the timeline from the Microsoft Intune admin center, you may run across one of these errors.

### The necessary configuration is missing in Microsoft Entra ID

**Error message:** The necessary configuration is missing in Microsoft Entra ID. Make sure to attach the Configuration Manager site to your Azure tenant, and assign the proper user role in Microsoft Entra ID.

**Possible causes:**

- Make sure [Microsoft Entra user discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc) and [Active Directory User discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) are configured and the user account accessing tenant attach features from the Microsoft Intune admin center is discovered by both.
- The user account might need an [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned.

### Unable to get timeline information

**Error message:** Unable to get timeline information. Make sure the Microsoft Entra ID and AD user discovery are configured and the user is discovered by both. Verify the user has the proper permissions in Configuration Manager.

**Possible causes:**

Verify the account has the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission under **Collection** in Configuration Manager.
- The **Notify Resource** permission under **Collection** in Configuration Manager.

  - This permission is needed to be able to sync the latest events.

### Unable to get timeline information

**Error message:** The device information hasn't yet synchronized from Configuration Manager to Microsoft Intune admin center. Wait up to 15 minutes after you attach the site to your Azure tenant.

**Possible resolution:** Wait for approximately 15 minutes and the issue should be resolved automatically.

### Unexpected error occurred

**Error message:** Unexpected error occurred

**Possible causes:**

- Verify you have a supported version of Configuration Manager and the corresponding version of the console installed.
- If there are a large number of events \(more than 10,000, approximately\), and multiple searches are requested rapidly, then it's possible to receive an unexpected error. You may also see your search results [timeout](#bkmk_timeout).

### Getting results timed out

**Error message:** Getting results timed out. Make sure that the Configuration Manager service connection point is operational and has a connection to the cloud.

**Possible cause:** If there are a large number of events \(more than 10,000, approximately\), and multiple searches are requested rapidly, then it's possible to see a timeout. You may also see an [unexpected error](#bkmk_500).

## Known issues

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).

## Next steps

[Troubleshoot tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot)
