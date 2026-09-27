<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/edge-data-security/app-configuration-step-4 -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Step 4: App Configuration Policies for Microsoft Edge for Business

App configuration policies \(ACP\) customize Microsoft Edge for Business behavior and features on each platform. In the Secure Enterprise Browser plan, ACPs work alongside App Protection Policies \(Step 2\) and Conditional Access \(Step 1\) to deliver a layered, Zero Trust browser experience on managed and BYOD devices.

This step defines three progressive ACP configurations per platform, Level 1 \(Basic\), Level 2 \(Enhanced\), and Level 3 \(High\), so you can standardize user experience, lock down risky surfaces, and align restrictions to data sensitivity and user risk. These policies complement data-protection controls \(APP\) rather than replace them.

Note

App configuration policies customize browser features and behavior. They complement app protection policies that focus on data protection.

## Policy Selection Based on Device Enrollment

App Configuration Policies \(this step\) are designed for non-enrolled devices using the Managed Apps configuration channel, while Settings Catalog policies \(Step 5\) are designed for enrolled devices with device-level controls.

Important

Choose the appropriate policy type based on device enrollment status to avoid policy conflicts.

## Security Level Selection

The three security levels \(Level 1, 2, 3\) are not cumulative - they represent progressively stricter configurations designed for different user roles and data sensitivity requirements.

### Implementation Guidance

- Evaluate your scenarios and user roles to determine which level is appropriate for each user group
- Deploy only one level per user/device, not all three levels simultaneously
- Align security level assignment with business role and data access requirements

### Example Assignments

- **Level 1 \(Basic\)**: General users, standard productivity workflows \(~80% of users\)
- **Level 2 \(Enhanced\)**: Finance, HR, IT staff handling sensitive data \(~15% of users\)
- **Level 3 \(High\)**: Executives, SecOps, Legal, users with access to highly confidential data \(~5% of users\)

## App configuration policies for Windows

Windows app configuration policies provide browser customization through managed app settings.

> **Microsoft Documentation:**
> 
> - [Microsoft Edge Browser Policies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies)
> - [Windows App Configuration Policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview)
> - [Managed App Configuration for Windows](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps)

**Prerequisites:**

- Windows 11
- Microsoft Edge installed
- Intune enrollment or MAM managed
- User Entra ID account

### Level 1 - Basic browser configuration for Windows

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Windows ACP Level 1 Basic
   - **Description:** Enhanced browser customization for Microsoft Edge Windows with comprehensive basic controls addressing ACP gap analysis

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| HomepageLocation | `https://portal.company.com` | [Configure the home page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
| ShowHomeButton | Enabled | [Show Home button on toolbar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
| NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
| RestoreOnStartup | Open the new tab page \(5\) | [Action to take on startup](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
| HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
| DefaultPopupsSetting | Do not allow popups \(2\) | [Default pop-up window setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
| PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
| AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
| AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| TrackingPrevention | Balanced \(2\) | [Block tracking of users' web-browsing activity](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
| DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
| DefaultSearchProviderName | Microsoft Bing | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| NetworkPredictionOptions | Don't predict \(2\) | [Enable network prediction](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
| ImportAutofillFormData | Disabled | [Allow importing of autofill form data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
| ImportSavedPasswords | Disabled | [Allow importing of saved passwords](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
| ImportBrowsingHistory | Disabled | [Allow importing of browsing history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
| ImportCookies | Disabled | [Allow importing cookies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
| ImportExtensions | Disabled | [Allow importing of extension](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
| ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
| ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
| ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
| DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
| PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
| DownloadRestrictions | Block malicious downloads and dangerous file types | [Allow download restrictions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
| ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
| EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
| EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
| FavoritesBarEnabled | Enabled | [Show favorites bar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
| AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |

8. Select **Next**.
9. For **Assignments**, assign to **SEB-Level1-Users** group.
10. Select **Next** to review the settings. Then choose **Create**.

### Level 2 - Enhanced browser configuration for Windows

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Windows ACP Level 2 Enhanced
   - **Description:** Advanced browser customization with enhanced security controls and comprehensive feature management

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| HomepageLocation | `https://portal.company.com` | [Configure the home page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
| ShowHomeButton | Enabled | [Show Home button on toolbar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
| NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
| RestoreOnStartup | Open the new tab page \(5\) | [Action to take on startup](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
| HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
| DefaultPopupsSetting | Do not allow popups \(2\) | [Default pop-up window setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
| PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
| AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
| AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| TrackingPrevention | Balanced \(2\) | [Block tracking of users' web-browsing activity](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
| DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
| DefaultSearchProviderName | Microsoft Bing | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| NetworkPredictionOptions | Don't predict \(2\) | [Enable network prediction](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
| ImportAutofillFormData | Disabled | [Allow importing of autofill form data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
| ImportSavedPasswords | Disabled | [Allow importing of saved passwords](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
| ImportBrowsingHistory | Disabled | [Allow importing of browsing history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
| ImportCookies | Disabled | [Allow importing cookies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
| ImportExtensions | Disabled | [Allow importing of extension](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
| ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
| ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
| ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
| DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
| PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
| DownloadRestrictions | Block malicious downloads and dangerous file types | [Allow download restrictions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
| ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
| EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
| EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
| FavoritesBarEnabled | Enabled | [Show favorites bar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
| AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |
| SmartScreenForTrustedDownloadsEnabled | Enabled | [Force Microsoft Defender SmartScreen checks on downloads from trusted sources](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/smartscreenfortrusteddownloadsenabled) |
| InsecureContentAllowedForUrls | `[]` | [Allow insecure content on specified sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentallowedforurls) |
| InsecureContentBlockedForUrls | `["*"]` | [Block insecure content on specified sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentblockedforurls) |
| ExtensionInstallAllowlist | `[]` | [Allow specific extensions to be installed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallallowlist) |
| ExtensionInstallForcelist | `[]` | [Control which extensions are installed silently](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallforcelist) |
| ExtensionSettings | `{"*":{"installation_mode":"blocked"}}` | [Configure extension management settings](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensionsettings) |
| NativeMessagingAllowlist | `[]` | [Control which native messaging hosts users can use](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingallowlist) |
| NativeMessagingHostBlocklist | `["*"]` | [Configure native messaging block list](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingblocklist) |
| AutoSelectCertificateForUrls | `["*.company.com"]` | [Automatically select client certificates for these sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autoselectcertificateforurls) |
| WebRtcUdpPortRange | 10000:11000 | [Restrict the range of local UDP ports used by WebRTC](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webrtcudpportrange) |
| DefaultImagesSetting | Allow images \(1\) | [Default images setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultimagessetting) |
| DefaultJavaScriptSetting | Allow JavaScript \(1\) | [Default JavaScript setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
| ClearBrowsingDataOnExit | Enabled | [Clear browsing data when Microsoft Edge closes](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/clearbrowsingdataonexit) |
| SyncDisabled | Enabled | [Disable synchronization of data using Microsoft sync services](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/syncdisabled) |
| PrintingEnabled | Enabled | [Enable printing](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/printingenabled) |
| InPrivateModeAvailability | InPrivate mode available \(0\) | [InPrivate mode availability](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/inprivatemodeavailability) |
| ForceSync | Disabled | [Force synchronization of browser data and do not show the sync consent prompt](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/forcesync) |
| SleepingTabsEnabled | Enabled | [Configure sleeping tabs](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/sleepingtabsenabled) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| LocalProvidersEnabled | Disabled | [Allow suggestions from local providers](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/localprovidersenabled) |
| VideoCaptureAllowed | Disabled | [Allow or block video capture](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/videocaptureallowed) |
| DefaultNotificationsSetting | Block \(2\) | [Default notification setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultnotificationssetting) |
| DefaultGeolocationSetting | Don't allow sites to track users' physical location \(2\) | [Default geolocation setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
| WebUsbAllowDevicesForUrls | `[]` | [Allow WebUSB on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webusballowdevicesforurls) |
| WebUsbBlockedForUrls | `[{"urls": ["*"], "devices": [{"vendor_id": "*", "product_id": "*"}]}]` | [Block WebUSB on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webusbblockedforurls) |
| WebRtcLocalhostIpHandling | Disable non-proxied UDP \(default\_public\_interface\_only\) | [Restrict exposure of local IP address by WebRTC](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webrtclocalhostiphandling) |

8. Select **Next**.
9. For **Assignments**, assign to **SEB-Level2-Users** group.
10. Select **Next** to review the settings. Then choose **Create**.

### Level 3 - High security configuration for Windows

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Windows ACP Level 3 High
   - **Description:** High browser customization with complete enterprise controls, zero-trust configuration, and comprehensive security isolation

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:
   | Name | Value | Documentation |
   | --- | --- | --- |
   | HomepageLocation | `https://portal.company.com` | [Configure the home page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
   | ShowHomeButton | Enabled | [Show Home button on toolbar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
   | NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
   | RestoreOnStartup | Open the new tab page \(5\) | [Action to take on startup](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
   | HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
   | DefaultPopupsSetting | Do not allow popups \(2\) | [Default pop-up window setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
   | PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
   | AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
   | AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
   | TrackingPrevention | Balanced \(2\) | [Block tracking of users' web-browsing activity](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
   | DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
   | DefaultSearchProviderName | Microsoft Bing | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
   | DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
   | SearchSuggestEnabled | Disabled | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
   | ImportAutofillFormData | Disabled | [Allow importing of autofill form data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
   | ImportSavedPasswords | Disabled | [Allow importing of saved passwords](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
   | ImportBrowsingHistory | Disabled | [Allow importing of browsing history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
   | ImportCookies | Disabled | [Allow importing cookies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
   | ImportExtensions | Disabled | [Allow importing of extension](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
   | ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
   | ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
   | ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
   | DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
   | PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
   | HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
   | ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
   | EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
   | EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
   | FavoritesBarEnabled | Enabled | [Show favorites bar](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
   | AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |
   | SmartScreenForTrustedDownloadsEnabled | Enabled | [Force Microsoft Defender SmartScreen checks on downloads from trusted sources](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/smartscreenfortrusteddownloadsenabled) |
   | InsecureContentAllowedForUrls | \[\] | [Allow insecure content on specified sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentallowedforurls) |
   | InsecureContentBlockedForUrls | \["\*"\] | [Block insecure content on specified sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentblockedforurls) |
   | ExtensionInstallAllowlist | \[\] | [Allow specific extensions to be installed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallallowlist) |
   | ExtensionInstallForcelist | \[\] | [Control which extensions are installed silently](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallforcelist) |
   | ExtensionSettings | {"\*":{"installation\_mode":"blocked"}} | [Configure extension management settings](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/extensionsettings) |
   | NativeMessagingAllowlist | \[\] | [Control which native messaging hosts users can use](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingallowlist) |
   | NativeMessagingBlocklist | \["\*"\] | [Configure native messaging block list](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingblocklist) |
   | AutoSelectCertificateForUrls | \["\*.company.com"\] | [Automatically select client certificates for these sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autoselectcertificateforurls) |
   | WebRtcUdpPortRange | 10000:11000 | [Restrict the range of local UDP ports used by WebRTC](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webrtcudpportrange) |
   | DefaultImagesSetting | Allow images \(1\) | [Default images setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultimagessetting) |
   | DefaultJavaScriptSetting | Allow JavaScript \(1\) | [Default JavaScript setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
   | SyncDisabled | Enabled | [Disable synchronization of data using Microsoft sync services](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/syncdisabled) |
   | ForceSync | Disabled | [Force synchronization of browser data and do not show the sync consent prompt](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/forcesync) |
   | SleepingTabsEnabled | Enabled | [Configure sleeping tabs](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/sleepingtabsenabled) |
   | SearchSuggestEnabled | Disabled | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
   | LocalProvidersEnabled | Disabled | [Allow suggestions from local providers](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/localprovidersenabled) |
   | DefaultNotificationsSetting | Block \(2\) | [Default notification setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultnotificationssetting) |
   | DefaultGeolocationSetting | Don't allow sites to track users' physical location \(2\) | [Default geolocation setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
   | WebUsbBlockedForUrls | \[\] | [Allow WebUSB on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webusballowdevicesforurls) |
   | WebUsbBlockDevicesForUrls | \[{"urls":\["*"\],"devices":\[{"vendor\_id":"*","product\_id":"\*"}\]}\] | [Block WebUSB on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webusbblockedforurls) |
   | WebRtcLocalhostIpHandling | Disable non-proxied UDP \(default\_public\_interface\_only\) | [Restrict exposure of local IP address by WebRTC](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/webrtclocalhostiphandling) |
   | URLAllowlist | \["*.company.com", "*.microsoft.com", "\*.office.com"\] | [Define a list of allowed URLs](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/urlallowlist) |
   | URLBlocklist | \["\*"\] | [Block access to a list of URLs](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/urlblocklist) |
   | CookiesAllowedForUrls | \["\*.company.com"\] | [Allow cookies on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/cookiesallowedforurls) |
   | CookiesBlockedForUrls | \["\*"\] | [Block cookies on specific sites](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/cookiesblockedforurls) |
   | CookiesSessionOnlyForUrls | \["\*"\] | [Limit cookies from specific websites to current session](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/cookiessessiononlyforurls) |
   | DownloadRestrictions | Block all downloads \(4\) | [Download restrictions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
   | ScreenCaptureAllowed | Disabled | [Allow or deny screen capture](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/screencaptureallowed) |
   | PrintingEnabled | Disabled | [Enable printing](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/printingenabled) |
   | DefaultClipboardSetting | Block clipboard \(2\) | [Default clipboard site permission](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultclipboardsetting) |
   | VideoCaptureAllowed | Disabled | [Allow or block video capture](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/videocaptureallowed) |
   | InPrivateModeAvailability | InPrivate mode forced \(2\) | [Configure InPrivate mode availability](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/inprivatemodeavailability) |
   | ClearBrowsingDataOnExit | Enabled | [Clear browsing data when Microsoft Edge closes](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/clearbrowsingdataonexit) |
   | SavingBrowserHistoryDisabled | Enabled | [Disable saving browser history](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/savingbrowserhistorydisabled) |
   | DeveloperToolsAvailability | Disallowed \(2\) | [Control where developer tools can be used](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/developertoolsavailability) |
   | NetworkPredictionOptions | Don't predict \(2\) | [Enable network prediction](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
   | EdgeCollectionsEnabled | Disabled | [Enable the Collections feature](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgecollectionsenabled) |
8. Select **Next**.
9. For **Assignments**, assign to **SEB-Level3-Users** group.
10. Select **Next** to review the settings. Then choose **Create**.

### Validation \(All Windows Levels\)

#### Policy Application

- In the Intune admin center, verify the Settings Catalog, Security Baseline, APP, and ACP policy deployment status for the targeted Windows devices.

#### Endpoint Verification

- On the client device, open Microsoft Edge and navigate to `edge://policy`.
- Confirm that all configured policy keys appear with expected values and don't show an **Error** state.

#### URL and Feature Enforcement

- **Level 1:** Confirm core security controls are active, including SmartScreen, tracking prevention, and basic restriction settings.
- **Level 2:** Validate enhanced restrictions such as extension blocking, data sync restrictions, and clear-on-exit behaviors.
- **Level 3:** Attempt to browse to nonallowlisted URLs and verify they're blocked or isolated \(for example, Application Guard\).

#### Update Policies

- In `edge://policy`, search for **Update** to ensure the configured update behavior \(for example, daily checks, suppressed hours, version pinning\) matches the assigned security level.

#### Isolation Controls \(Level 3 Only\)

- Verify that high-risk or unapproved URLs trigger the expected isolation behavior, such as forced application isolation or a secure browsing container.

## App Configuration Policies for Android

Android app configuration policies customize Microsoft Edge for Business behavior on mobile devices. These policies define browser defaults, restrict risky features, and enforce privacy protections in alignment with enterprise security frameworks.

> **Microsoft Documentation:**
> 
> - [Microsoft Edge Mobile Policies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies)
> - [Android App Configuration Policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview)
> - [Managed App Configuration for Android](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps)

**Prerequisites:**

- Android 10.0+ \(8.0+ for userless devices\)
- Microsoft Edge for Android installed
- Company Portal or Intune app installed
- Microsoft Intune license assigned to the user
- Device MAM-enabled or MDM-enrolled through Intune
- User signed in with Microsoft Entra ID account

### Level 1 – Basic Mobile Browser Configuration for Android

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Android ACP Level 1 Basic
   - **Description:** Basic browser configuration for Microsoft Edge Android with essential security settings and fundamental mobile controls

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge \(Android\)**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam  <br>.managedbrowser.PasswordSSO | true | [Microsoft Entra password single sign-on](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android#microsoft-entra-password-single-sign-on) |
| com.microsoft.intune.mam  <br>.managedbrowser.SmartScreenEnabled | true | [Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | true | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | false | [Disable password import](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 0 | [Configure new tab page layout](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | false | [Enable kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | true | [Show address bar in kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [Enable SmartScreen](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Enable translate](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | true | [Allow SSL error override](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | true | [Enable as default browser](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | true | [Enable Edge Copilot](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 1 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| DefaultCookiesSetting | 1 | [Default cookies setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultcookiessetting) |
| BiometricAuthenticationBeforeFilling | false | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeBrandLogo | true | [Enable Edge brand logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "direct"} | [Configure proxy settings](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |

8. Under Microsoft Tunnel for Mobile Application Management settings:

| Name | Value |
| --- | --- |
| Tunnel enabled | Not configured |
| Connection name | Not configured |
| Microsoft Tunnel site | Not configured |
| Per-App VPN \(Android only\) | No Per-App VPN |
| Automatic configuration script | Not configured |
| Address | Not configured |
| Port Number | Not configured |
| Root Certificate | Not configured |

9. Expand **Edge configuration settings** and configure:

| Name | Value |
| --- | --- |
| Application proxy redirection | Disable |
| Homepage shortcut URL | `https://www.company.com` |
| Managed bookmarks | Company Portal \| `https://portal.company.com` |
| Allowed URLs | Leave empty \(Level 3 uses Allowed URLs\) |
| Blocked URLs | Leave empty \(Level 2 uses Blocked URLs\) |
| Redirect restricted sites to personal context | Disable |

10. Select **Next**
11. In **Assignments**, assign to **SEB-Level1-Users** group.
12. Select **Next** to review the settings. Then choose **Create**.

### Level 2 – Enhanced Mobile Browser Configuration for Android

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Android ACP Level 2 Enhanced
   - **Description:** Enhanced browser configuration for Microsoft Edge Android with more security controls and data protection features

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge \(Android\)**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam  <br>.managedbrowser.PasswordSSO | true | [Microsoft Entra password single sign-on](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android#microsoft-entra-password-single-sign-on) |
| com.microsoft.intune.mam  <br>.managedbrowser.SmartScreenEnabled | true | [Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | true | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 1 | [Configure new tab page layout](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | false | [Enable kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | true | [Show address bar in kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [Enable SmartScreen](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Enable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Enable translate](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [Allow SSL error override](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | false | [Set as default browser](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Enable Edge Copilot](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | false | [Disable browser history saving](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| DefaultCookiesSetting | 2 | [Default cookies setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultcookiessetting) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeBrandLogo | true | [Enable Edge brand logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "direct"} | [Configure proxy settings](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |
| EdgeDisabledFeatures | password\|autofill\|copilot\|collections\|readaloud | [Disable features](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |

8. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | Leave empty \(Level 2 uses blocked URLs instead – when blocked URLs are configured, allowed URLs field becomes unavailable\) |
| Blocked URLs | \*.facebook.com, \*.twitter.com, \*.instagram.com, \*.tiktok.com |
| Redirect restricted sites to personal context | Enable |

9. Select **Next**
10. In **Assignments**, assign to **SEB-Level2-Users** group.
11. Select **Next** to review the settings. Then choose **Create**.

### Level 3 – High Security Mobile Configuration for Android

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge Android ACP Level 3 High
   - **Description:** High security browser configuration for Microsoft Edge Android with maximum restrictions, strict isolation, and comprehensive privacy controls

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge \(Android\)**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam  <br>.managedbrowser.PasswordSSO | false | [Microsoft Entra password single sign-on](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam  <br>.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | false | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable importing passwords](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 2 | [Configure new tab page layout](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | true | [Enable kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | false | [Show address bar in kiosk mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| EdgeSyncDisabled | true | [Disable browser sync](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| InPrivateModeAvailability | 1 | [Disable InPrivate mode](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#inprivatemodeavailability) |
| SavingBrowserHistoryDisabled | true | [Disable browser history saving](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| TranslateEnabled | false | [Disable translate](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeSharedDeviceSupportEnabled | false | [Disable shared device support](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| AutofillCreditCardEnabled | false | [Disable autofill for payment instructions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| DownloadRestrictions | 2 | [Download restrictions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultBrowserSettingEnabled | false | [Set as default browser](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Enable Edge Copilot](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| DefaultCookiesSetting | 4 | [Default cookies setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultcookiessetting) |
| DefaultJavaScriptSetting | 2 | [Default JavaScript setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
| DefaultGeolocationSetting | 2 | [Default geolocation setting](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeDisabledFeatures | inprivate\|autofill\|password\|translator\|readaloud\|drop\|  <br>coupons\|extensions\|copilot\|collections\|myapps | [Disable features](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBrandLogo | true | [Enable Edge brand logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "fixed\_servers"} | [Configure proxy settings](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |
| EdgeBlockSignInEnabled | true | [Block sign-in enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeblocksigninenabled) |

8. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | \*.company.com, \*.microsoft.com, login.microsoftonline.com |
| Blocked URLs | Leave empty \(Level 3 uses allowed URLs – when allowed URLs are configured, blocked URLs field becomes unavailable\) |

9. Select **Next**
10. In **Assignments**, assign to **SEB-Level3-Users** group.
11. Select **Next** to review the settings. Then choose **Create**.

### Validation \(All Android Levels\)

#### Policy Application

- In the Intune admin center, verify the ACP deployment status for assigned Android devices.

#### Browser Configuration

- On an Android device, open Microsoft Edge and go to `edge://policy` to confirm the expected configuration values are present and not marked as errors.

#### URL Filtering

- **Level 1:** Confirm allowed URLs operate as expected.
- **Level 2:** Confirm blocked URLs \(such as social media domains\) are restricted.
- **Level 3:** Confirm only allowlisted corporate URLs are accessible.

#### Feature Restrictions

- Validate restricted features based on the assigned security level, such as InPrivate mode, autofill, password import, extensions, and Copilot visibility.

#### Homepage and Bookmarks

- Confirm the managed homepage and managed bookmarks appear correctly in Microsoft Edge.

#### Security Settings

- Verify that SmartScreen, HTTPS enforcement, and data-sharing restrictions operate according to the applied policy.

#### VPN Integration \(If Configured\)

- For deployments using Microsoft Tunnel, ensure per-app VPN settings connect and route traffic as defined in the ACP.

## App Configuration Policies for iOS/iPadOS

iOS app configuration policies define and enforce browser behavior for Microsoft Edge for Business on iPhone and iPad devices. These policies provide progressive control over privacy, security, and data protection while aligning with Zero Trust principles.

> **Microsoft Documentation:**
> 
> - [Microsoft Edge Mobile Policies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies)
> - [iOS App Configuration Policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview)
> - [Managed App Configuration for iOS](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps)

**Prerequisites:**

- iOS/iPadOS 17+
- Microsoft Edge for iOS installed
- Company Portal or Intune app installed
- Microsoft Intune license assigned to the user
- Device MAM-enabled or MDM-enrolled through Intune
- User signed in with Microsoft Entra ID account

Important

In iOS App Configuration Policies, **Allowed URLs** and **Blocked URLs** are mutually exclusive. When you configure one, the other becomes unavailable.

### Level 1 – Basic mobile browser configuration for iOS

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge iOS ACP Level 1 Basic
   - **Description:** Basic browser configuration for Microsoft Edge iOS with essential security settings and fundamental mobile controls

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge**.
   - Choose **Microsoft Edge \(iOS/iPadOS\)**, then **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Password single sign-on](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | true | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | false | [Disable password import](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | false | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Translate enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | true | [SSL error override allowed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | true | [Default browser setting enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| ExperimentationAndConfigurationServiceControl | 1 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeNetworkStackPref | 0 | [Edge network stack preference](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |

8. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Application proxy redirection | Disable |
| Homepage shortcut URL | `https://www.company.com` |
| Managed bookmarks | Company Portal \| `https://portal.company.com` |
| Allowed URLs | Leave empty \(Level 3 uses Allowed URLs\) |
| Blocked URLs | Leave empty \(Level 2 uses Blocked URLs\) |
| Redirect restricted sites to personal context | Disable |

9. Select **Next**.
10. In **Assignments**, assign to **SEB-Level1-Users** group.
11. Select **Next** to review the settings. Then choose **Create** when you're done.

### Level 2 – Enhanced mobile browser configuration for iOS

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge iOS ACP Level 2 Enhanced
   - **Description:** Enhanced browser configuration for Microsoft Edge iOS with more security controls and data protection features

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge**.
   - Choose **Microsoft Edge \(iOS/iPadOS\)**, then **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Password single sign-on](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | true | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Translate enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeNetworkStackPref | 0 | [Network stack preference](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |
| DefaultBrowserSettingEnabled | false | [Default browser setting enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Disable Edge Copilot](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | false | [Disable browser history saving](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeDisabledFeatures | password\|autofill\|copilot\|collections\|readaloud | [Disable features](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBlockSignInEnabled | false | [Block sign-in enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeblocksigninenabled) |

8. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | Leave empty \(Level 2 uses blocked URLs instead – when blocked URLs are configured, allowed URLs field becomes unavailable\) |
| Blocked URLs | \*.facebook.com, \*.twitter.com, \*.instagram.com, \*.tiktok.com |
| Redirect restricted sites to personal context | Enable |

9. Select **Next**.
10. In **Assignments**, assign to **SEB-Level2-Users** group.
11. Select **Next** to review the settings. Then choose **Create** when you're done.

### Level 3 – High security mobile configuration for iOS

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Manage apps** > **Configuration** > **Create** > **Managed apps**.
3. On the **Basics** tab, enter:

   - **Name:** Edge iOS ACP Level 3 High
   - **Description:** High security browser configuration for Microsoft Edge iOS with maximum restrictions, strict isolation, and comprehensive privacy controls

4. In **Target policy to**, select **Selected apps**.

   - Choose **+ Select public apps**.
   - In the **Select apps to target** panel, search for and select **Microsoft Edge \(iOS/iPadOS\)**, then select **Select**.

5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | false | [Password single sign-on](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | false | [Enable EdgeMyApps](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | false | [Translate enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeNetworkStackPref | 0 | [Network stack preference](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |
| DefaultBrowserSettingEnabled | false | [Default browser setting enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Disable Edge Copilot](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | false | [Disable shared device support](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | true | [Disable browser history saving](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeDisabledFeatures | inprivate\|autofill\|password\|translator\|readaloud\|drop\|  <br>coupons\|extensions\|copilot\|collections\|myapps\|share | [Disable features](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBlockSignInEnabled | true | [Block sign-in enabled](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/edgeblocksigninenabled) |

8. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | \*.company.com, \*.microsoft.com, login.microsoftonline.com |
| Blocked URLs | Leave empty \(Level 3 uses allowed URLs – when allowed URLs are configured, blocked URLs field becomes unavailable\) |

9. Per-App VPN \(optional\): Integrate with Microsoft Tunnel if necessary for isolated secure traffic routing
10. Select **Next**.
11. In **Assignments**, assign to **SEB-Level3-Users** group.
12. Select **Next** to review the settings. Then choose **Create** when you're done.

### Validation \(All iOS Levels\)

#### Policy Application

- In the Intune admin center, verify the assigned App Protection and App Configuration policies have successfully deployed to the targeted iOS devices.

#### App Configuration Verification

- On the device, open Microsoft Edge and navigate to **Settings**.
- Confirm that managed configuration values—such as homepage, search provider, password manager, and disabled features—match the applied ACP settings.

#### URL Filtering

- **Level 1:** Confirm that allowed URLs operate as expected.
- **Level 2:** Verify that blocked URL categories \(for example, social media domains\) can't be accessed.
- **Level 3:** Confirm that only the configured corporate allowlisted URLs are accessible.

#### Feature Restrictions

- Validate restricted features based on the assigned level, including:

  - **Level 1:** SmartScreen, pop-up blocking, and basic security controls.
  - **Level 2:** Sync disabled, password import blocked, biometric authentication for filling enabled, InPrivate browsing controlled.
  - **Level 3:** InPrivate disabled, history saving disabled, shared device mode disabled, and advanced restrictions \(such as Collections, Extensions, Drop, Copilot\) enforced.

#### Homepage and Bookmarks

- Confirm that the managed homepage and any configured managed bookmarks appear correctly in Microsoft Edge.

#### Policy Dependency Check

- Ensure the user is signed in to Edge using their work or school \(Entra ID\) account, as App Configuration settings only apply within the managed work profile context.

## Next step

Continue to [Step 5](https://learn.microsoft.com/en-us/intune/solutions/edge-data-security/settings-catalog-step-5) to configure Settings Catalog policies for enrolled Windows and macOS devices.
