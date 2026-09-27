<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/compliance/plan-design/plan-for-and-configure-compliance-settings -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Plan for and configure compliance settings in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Before you start working with Configuration Manager compliance settings, there are a few prerequisites you need to know about, and some configuration tasks you'll need to perform.

## Prerequisites for compliance settings

| Prerequisite | More information |
| --- | --- |
| Windows Configuration Manager clients must be enabled and configured for compliance evaluation. | See below |
| If you want to run reports, then you must configure reporting for your site. | [Introduction to reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting) |
| Required security permissions. | The **Compliance Settings Manager** security role includes the necessary permissions to manage compliance settings, user data and profiles configuration items, and remote connection profiles.  <br>  <br>[Configure role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration) |

## Enable and configure compliance settings \(for Windows PCs only\)

This procedure configures the default client settings for compliance settings and applies to all computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers for which you want to use compliance settings. For more information about how to create custom device settings, see [How to configure client settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-settings).

Tip

Other device types require no specific configuration to evaluate compliance settings.

1. In the Configuration Manager console, click **Administration** > **Client Settings** > **Default Settings**.
2. On the **Home** tab, in the **Properties** group, click **Properties**.
3. In the **Default Settings** dialog box, click **Compliance Settings**.
4. Configure the following client settings for compliance settings:

   - **Enable compliance evaluation on clients** - Set to **True** if you want to evaluate compliance on client devices.
   - **Schedule compliance evaluation** - Click **Schedule** if you want to modify the default compliance evaluation schedule on client devices.
   - **Enable User Data and Profiles** - Enable this option if you want to create and deploy user data and profiles configuration items to Windows computers. For details, see [Create user data and profiles configuration items](https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/create-remote-connection-profiles).

5. Click **OK** to close the **Default Settings** dialog box.

Client computers are configured with these settings the next time they download client policy.
