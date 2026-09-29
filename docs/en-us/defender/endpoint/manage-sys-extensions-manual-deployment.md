<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-sys-extensions-manual-deployment -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Manage system extensions using the manual methods of deployment

When you deploy Microsoft Defender for Endpoint on macOS without a mobile device management \(MDM\) solution, you must manually approve system extensions and grant the required permissions. This article walks macOS administrators through approving system extensions, granting Accessibility and Full Disk Access permissions, enabling notifications, and verifying a healthy deployment state.

## Configure system extensions and permissions using manual deployment

### Approve system extensions manually

You might see the prompt that's shown in the following screenshot:

[![The system extensions blocked prompt screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/system-extension-blocked-prompt.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/system-extension-blocked-prompt.png#lightbox)

1. Select **OK**. You might get a second prompt as shown in the following screenshot:

   [![The second prompt regarding system extensions being blocked.](https://learn.microsoft.com/en-us/defender-endpoint/media/system-extension-blocked-second-prompt.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/system-extension-blocked-second-prompt.png#lightbox)
2. From this second-prompt screen, select **OK**. You receive a notification message that reads **Installation succeeded**, as shown in the following screenshot:

   [![The screen displaying the installation succeeded notification message.](https://learn.microsoft.com/en-us/defender-endpoint/media/installation-succeeded-notification-message.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/installation-succeeded-notification-message.png#lightbox)
3. On the screen displaying the **Installation succeeded** notification message, select **OK**. You return to the following screen:

   [![The Microsoft Defender for Endpoint menu containing the x symbol.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-menu.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-menu.png#lightbox)
4. From the menu bar, select the **x** symbol on the shield. You get the options shown in the following screenshot:

   [![The screen on clicking the x symbol in the shield.](https://learn.microsoft.com/en-us/defender-endpoint/media/options-on-clicking-x-symbol.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/options-on-clicking-x-symbol.png#lightbox)
5. Select **Action needed**. The following screen appears:

   [![The Virus & threat protection screen containing the Fix button.](https://learn.microsoft.com/en-us/defender-endpoint/media/virus-and-threat-protection-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/virus-and-threat-protection-screen.png#lightbox)
6. Select **Fix** in the upper-right corner of the **Virus & threat protection** screen. You get a prompt, as shown in the following screenshot:

   [![The prompt dialog box on the Virus & threat protection screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/prompt-on-virus-and-threat-protection-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/prompt-on-virus-and-threat-protection-screen.png#lightbox)
7. Enter your password and select **OK**.
8. Select  [![The System Preferences icon.](https://learn.microsoft.com/en-us/defender-endpoint/media/system-preferences-icon.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/system-preferences-icon.png#lightbox)

   The **System Preferences** screen appears.

   [![The System Preferences screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/system-preferences-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/system-preferences-screen.png#lightbox)
9. Select **Security & Privacy**. The **Security & Privacy** screen appears.

   [![The Security & Privacy screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/security-and-privacy-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/security-and-privacy-screen.png#lightbox)
10. Select **Click the lock to make changes**. You get a prompt as shown in the following screenshot:

    [![The prompt on the Security & Privacy screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/prompt-on-security-and-privacy-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/prompt-on-security-and-privacy-screen.png#lightbox)
11. Enter your password and click **Unlock**. The following screen appears:

    [![The screen that is displayed on clicking Unlock.](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-on-clicking-unlock.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-on-clicking-unlock.png#lightbox)
12. Select **Details**, next to **Some software system requires your attention before it can be used**.

    [![The screen that is displayed on clicking Details.](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-on-clicking-details.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-on-clicking-details.png#lightbox)
13. Check both the **Microsoft Defender** checkboxes, and select **OK**. You get two pop-up screens, as shown in the following screenshot:

    [![The popup that appears on checking both the checkboxes.](https://learn.microsoft.com/en-us/defender-endpoint/media/popup-after-checking-both-md-checkboxes.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/popup-after-checking-both-md-checkboxes.png#lightbox)
14. On the **"Microsoft Defender" Would like to Filter Network Content** pop-up screen, select **Allow**.
15. On the **Microsoft Defender wants to make changes** pop-up screen, enter your password and select **OK**.

If you run `systemextensionsctl list`, you see output similar to the following screenshot showing the registered system extensions:

[![The resultant screen of running the systemextensionsdcl list.](https://learn.microsoft.com/en-us/defender-endpoint/media/result-of-running-systemextenstionsctl-list.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/result-of-running-systemextenstionsctl-list.png#lightbox)

### Grant Accessibility permissions manually

Perform the following steps to grant Accessibility access to Microsoft Defender:

1. On the **Security & Privacy** screen, select the **Privacy** tab.

   [![The Privacy tab.](https://learn.microsoft.com/en-us/defender-endpoint/media/privacy-tab.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/privacy-tab.png#lightbox)
2. Select **Accessibility** from the left navigation pane, and select **+**.

   [![The Accessibility menu item and the Plus icon.](https://learn.microsoft.com/en-us/defender-endpoint/media/accessibility-and-plus-icon.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/accessibility-and-plus-icon.png#lightbox)
3. In the file selection dialog, select **Applications** from the **Favorites** pane in the left-side of the screen; select **Microsoft Defender**; and then select **Open** at the bottom-right of the screen.

   [![The process of selecting Applications and Microsoft Defender.](https://learn.microsoft.com/en-us/defender-endpoint/media/applications-md-options.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/applications-md-options.png#lightbox)
4. In the **Accessibility** list, check the **Microsoft Defender** checkbox.

   [![Checking the Microsoft Defender checkbox.](https://learn.microsoft.com/en-us/defender-endpoint/media/checking-md-checkbox.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/checking-md-checkbox.png#lightbox)

### Grant Full Disk Access manually

Perform the following steps to grant Full Disk Access to Microsoft Defender:

1. On the **Security & Privacy** screen, select the **Privacy** tab.
2. Select **Full Disk Access** from the left navigation pane, and then select the **Lock** icon.

   [![The Full Disk Access option in the menu and the Lock icon.](https://learn.microsoft.com/en-us/defender-endpoint/media/full-disk-access-and-lock-icon.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/full-disk-access-and-lock-icon.png#lightbox)
3. Confirm that the Microsoft Defender extension has full disk access; if not, check the **Microsoft Defender** checkbox.

   [![Checking the MD checkbox.](https://learn.microsoft.com/en-us/defender-endpoint/media/check-md-checkbox.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/check-md-checkbox.png#lightbox)

### Enable notifications manually

Use the following steps to enable notifications for Microsoft Defender:

1. From the **System Preferences** home screen, select **Notifications**.

   [![The Notifications option in the System Preferences screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/notifications-option.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/notifications-option.png#lightbox)

   The **Notifications** screen appears.
2. Select **Microsoft Defender** from the left navigation pane.
3. Enable the **Allow Notifications** option and select **Alerts**. No further changes are required; leave all other notification settings at their defaults.

   [![Selecting Microsoft Defender option from the Notifications screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/notifications-md.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/notifications-md.png#lightbox)

### Verify a healthy system state

#### Review mdatp health output

After completing the manual deployment steps, run `mdatp health` in Terminal to confirm that Microsoft Defender for Endpoint is running correctly. The following screenshot shows an example of healthy output. In a healthy system, real-time protection is enabled, definitions are up to date, and the system extensions are active.

[![The mdatp health output screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-health-output.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-health-output.png#lightbox)

#### Check the system extensions

In terminal, run the following command to check the system extensions:

`systemextensionsctl list`

The following screenshot shows the expected output of `systemextensionsctl list` on a healthy system:

[![The command to check the system extensions.](https://learn.microsoft.com/en-us/defender-endpoint/media/command-to-check-system-extensions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/command-to-check-system-extensions.png#lightbox)
