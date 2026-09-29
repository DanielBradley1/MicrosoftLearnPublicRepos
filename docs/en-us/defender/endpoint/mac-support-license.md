<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-support-license -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Troubleshoot license issues for Microsoft Defender for Endpoint on macOS

## No license found

When [Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac) is being deployed, an error message with an **x** on top of the Microsoft Defender for Endpoint on macOS shield appears.

Select the **x** symbol.

![Screenshot that shows the menu bar containing the x symbol on the Microsoft Defender for Endpoint on macOS shield.](https://learn.microsoft.com/en-us/defender-endpoint/media/error-mde-mac-deployment.png)

### Message

When you select the **x** symbol, you see options as shown in the following screenshot:

![Screenshot that shows the option that gets listed on selecting the x symbol.](https://learn.microsoft.com/en-us/defender-endpoint/media/x-symbol-menu-items.png)

When you select **Action needed**, you get the error message as shown in the following screenshot:

![Screenshot of the page displaying the No license found message and its description.](https://learn.microsoft.com/en-us/defender-endpoint/media/license-not-found-message.png)

You encounter this message in a different way: If you're using the terminal to enter **mdatp health** without the double quotes, the message as shown in the following screenshot is displayed:

![Screenshot of the product page on which the No license found warning message is displayed.](https://learn.microsoft.com/en-us/defender-endpoint/media/no-license-found-warning.png)

### Cause

- You can encounter an error if you've deployed and/or installed the Microsoft Defender for Endpoint on macOS package [Download installation packages](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually#download-installation-and-onboarding-packages), but you might not have run the configuration script that contains the license settings. See [Step 15: Check Device and Configuration status](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune#step-15-check-device-and-configuration-status). For information on troubleshooting in this scenario, see [If you didn't run the configuration script](#if-you-didnt-run-the-configuration-script).
- You can encounter an error message when the Microsoft Defender for Endpoint on macOS agent isn't up to date. For information on troubleshooting in this scenario, see [If Microsoft Defender for Endpoint on macOS isn't up to date](#if-microsoft-defender-for-endpoint-on-macos-isnt-up-to-date).
- You can encounter an error message if your offboard and reonboard macOS devices from Microsoft Defender for Endpoint on macOS.
- You can encounter an error message if a license isn't assigned to a user. For information on troubleshooting in this scenario, see [If a license isn't assigned to a user](#if-a-license-isnt-assigned-to-a-user).

### Solutions

#### If you didn't run the configuration script

This section describes the troubleshooting measures when the error/warning message is caused by nonexecution of the configuration script. The script contains the license settings when the Microsoft Defender for Endpoint on macOS package is installed and deployed.

Depending on the deployment management tool used, follow the tool-specific instructions to onboard the package \(register the license\) as described in the following table:

| Management | License deployment instructions \(Onboarding instructions\) |
| --- | --- |
| Intune | [Check Device and Configuration status](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune#step-15-check-device-and-configuration-status) |
| JamF | [Get the Microsoft Defender for Endpoint onboarding package](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package) |
| Other MDM | [License settings](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm#license-settings) |
| Manual installation | [Download installation and onboarding packages](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually#download-installation-and-onboarding-packages); and [Onboarding Package](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually#onboarding-package) |

Note

If the onboarding package runs correctly, the licensing information is located in `/Library/Application Support/Microsoft/Defender/com.microsoft.wdav.atp.plist`.

#### If Microsoft Defender for Endpoint on macOS isn't up to date

For scenarios where Microsoft Defender for Endpoint on macOS isn't up to date, you need to [update](https://learn.microsoft.com/en-us/defender-endpoint/mac-updates) the agent.

#### If Microsoft Defender for Endpoint on macOS has been offboarded

When the offboarding script is executed on the macOS, it saves a file in `/Library/Application Support/Microsoft/Defender/` and it's named `com.microsoft.wdav.atp.offboarding.plist`.

If the file exists, it prevents the macOS from being onboarded again. Delete the **com.microsoft.wdav.atp.offboarding.plist** running the onboarding script again.

#### If a license isn't assigned to a user

1. In the Microsoft Defender portal \(security.microsoft.com\), select **Settings**, and then select **Endpoints**.

   [![Screenshot of the Settings screen on which the Endpoints option is listed.](https://learn.microsoft.com/en-us/defender-endpoint/media/endpoints-option-on-settings-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/endpoints-option-on-settings-screen.png#lightbox)
2. Select **Licenses**.

   [![Screenshot of the Endpoints page from which the Licenses options can be selected.](https://learn.microsoft.com/en-us/defender-endpoint/media/selecting-licenses-option-from-endpoints-screen.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/selecting-licenses-option-from-endpoints-screen.png#lightbox)
3. Select **View and purchase licenses in the Microsoft 365 admin center**. The following screen in the Microsoft 365 admin center portal appears:

   [![Screenshot of the Microsoft 365 admin center portal page from which licenses can be purchased and assigned.](https://learn.microsoft.com/en-us/defender-endpoint/media/m365-admin-center-purchase-assign-licenses.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/m365-admin-center-purchase-assign-licenses.png#lightbox)
4. Check the checkbox of the license you want to purchase from Microsoft, and select it. The screen displaying detail of the chosen license appears:

   ![Screenshot of the product page from which you can select the option of assigning the purchased license.](https://learn.microsoft.com/en-us/defender-endpoint/media/resultant-screen-of-selecting-preferred-license.png)
5. Select the **Assign licenses** link.

   ![Screenshot of the product page from which you can select the Assign licenses link.](https://learn.microsoft.com/en-us/defender-endpoint/media/assign-licenses-link.png)

   The following screen appears:

   [![Screenshot of the page containing the + Assign licenses option.](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-containing-option-to-assign-licenses.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/screen-containing-option-to-assign-licenses.png#lightbox)
6. Select **+ Assign licenses**.
7. Enter the name or email address of the person to whom you want to assign this license. The following screen appears, displaying the details of the chosen license assignee and a list of options.

   ![Screenshot of the page displaying the assignee's details and a list of options.](https://learn.microsoft.com/en-us/defender-endpoint/media/assignee-details-and-options.png)
8. Check the checkboxes for **Microsoft 365 Advanced Auditing**, **Microsoft Defender XDR**, and **Microsoft Defender for Endpoint**. Then select **Save**.

On implementing these solution-options \(either of them\), if the licensing issues have been resolved, and then you run **mdatp health**, you should see the following results:

![Screenshot of the page containing the results displayed after running mdatp health.](https://learn.microsoft.com/en-us/defender-endpoint/media/results-after-license-issues-resolved.png)

## Sign in with your Microsoft account

![Screenshot of the page from which the users have to sign in with their Microsoft account's credentials to get started.](https://learn.microsoft.com/en-us/defender-endpoint/media/mac-consumer-login.png)

### Message

Sign in with your Microsoft account to get started.

Create new account or Switch to enterprise app.

### Cause

You've downloaded and installed [Microsoft Defender for individuals on macOS](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) on top of previously installed Microsoft Defender for Endpoint.

### Solution

Select **Switch to enterprise app** to switch to Enterprise experience.

You can also suppress switching to experience for Individuals on MDM-enrolled machines by including **userInterface**/**consumerExperience** in the Defender's settings:

```xml
<key>userInterface</key>
<dict>
    <key>consumerExperience</key>
    <string>disabled</string>
</dict>
```

## Recommended content

- [Manual deployment for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually): Install Microsoft Defender for Endpoint on macOS manually from the command line.
- [Set up the Microsoft Defender for Endpoint on macOS policies in Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies): Learn how to set up the Microsoft Defender for Endpoint on macOS policies in Jamf Pro.
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac): Learn how to install, configure, update, and use Microsoft Defender for Endpoint on Mac.
- [Deploying Microsoft Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf): Learn how to deploy Microsoft Defender for Endpoint on macOS with Jamf Pro.
