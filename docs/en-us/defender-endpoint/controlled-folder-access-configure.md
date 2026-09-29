<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-configure -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Configure controlled folder access \(CFA\)

[Controlled folder access](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview) \(CFA\) helps protect your valuable data from malicious apps and threats, such as ransomware, by preventing untrusted apps from changing files in protected folders. You can enable and configure CFA by using any of the methods in this article.

For best results, use an enterprise-level management solution such as Microsoft Intune or Microsoft Configuration Manager to manage CFA.

## Prerequisites

CFA is available in the following operating systems:

- Windows 10 or later.
- Windows Server 2019 or later.
- Windows Server 2016 and Windows Server 2012 R2 as part of the [modern, unified Microsoft Defender for Endpoint solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2).

## Configure CFA in Intune using endpoint security policies

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To configure CFA in Microsoft Intune, use an endpoint security **Attack surface reduction** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: Select **Manage** > **Attack surface reduction** on the **Endpoint security \| Overview** page.
- **Platform**: Select **Windows**.
- **Profile**: Select **Attack Surface Reduction Rules**.

When you create or modify the policy, after you configure the [attack surface reduction \(ASR\) rules settings](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-exclusions-in-intune-using-endpoint-security-policies), use these specific CFA settings on the **Configuration settings** tab:

- **Enable controlled folder access**: Select an available [mode value](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#modes-for-cfa). After you assess the effect of CFA in **Audit Mode**, you can set it to **Enabled**.
- **Controlled folder access protected folders**: To add more folders that get CFA protection, use either of the following methods:

  - Select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Add**. In the box that appears, enter the path to include. For example:

    - `C:\Data\Reports`
    - `C:\Data\Finance`

  - Select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-icon-import.png) **Import** to import a CSV file that contains the paths to include. The CSV file uses the following format:

    ```text
    ControlledFolderAccessProtectedFolders
    "C:\folder1"
    "C:\folder2"
    ...
    ```


    Tip


    Double quotation marks around the values are optional, and are ignored \(aren't used in the values\) if you include them. Don't use single quotation marks around the values.

- **Controlled folder access allowed applications**: To specify apps that are allowed to make changes to files in protected folders, use the same ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Add** or ![](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-icon-import.png) **Import** methods described for **Controlled folder access protected folders**, specifying the path and file name of each app.

  The CSV file uses the following format:

  ```text
  ControlledFolderAccessAllowedApplications
  "C:\Apps\app1.exe"
  "%ProgramFiles%\Fabrikam\DriveManager\*\DriveService.exe"
  ...
  ```


  The path of each app can include environment variables and wildcards, as described in [Allow apps to modify files in protected folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders).

For more information about attack surface reduction profiles in Microsoft Intune, see [Manage attack surface reduction settings with Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-asr-policy#attack-surface-reduction-profiles).

## Configure CFA in the Microsoft Defender portal

If your organization [manages endpoint security policies in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure), you can configure CFA with the same endpoint security policies that Intune uses.

For detailed instructions, see [Create an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#create-an-endpoint-security-policy) or [Edit an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#edit-an-endpoint-security-policy) \(links open new tabs\).

When you create the policy on the **Windows policies** tab of the **Endpoint security policies** page in the Defender portal at [https://security.microsoft.com/policy-inventory?osPlatform=Windows](https://security.microsoft.com/policy-inventory?osPlatform=Windows), use these specific settings:

- **Select platform**: Select **Windows**.
- **Select template**: Select **Attack surface reduction rules**.

When you create or modify the policy, use the same CFA settings described in [Configure CFA in Intune using endpoint security policies](#configure-cfa-in-intune-using-endpoint-security-policies) on the **Configuration settings** tab.

When you assign the policy, assignment group limitations apply to devices managed through security settings management. For details, see the [Assignments step](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#create-an-endpoint-security-policy).

## Configure CFA in any MDM solution using the Policy CSP

The Policy configuration service provider \(CSP\) enables enterprise organizations to configure CFA on Windows devices using any mobile device management \(MDM\) solution, not just Microsoft Intune. For more information, see [Policy CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider).

Use the following CSPs from the [Policy CSP - Defender](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender) area to configure CFA.

### Enable CFA using the Policy CSP

Use the [EnableControlledFolderAccess](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#enablecontrolledfolderaccess) CSP to configure CFA and select the protection mode.

**OMA-URI path**: `./Device/Vendor/MSFT/Policy/Config/Defender/EnableControlledFolderAccess`  
**Value**: Enter one of the following [mode values](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#modes-for-cfa):

- `0`: Disabled \(default\).
- `1`: Enabled \(block\).
- `2`: Audit Mode.
- `3`: Block disk modification only.
- `4`: Audit disk modification only.

### Add folders to protected folders using the Policy CSP

CFA protects [an unmodifiable list of common folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#default-folders-protected-by-cfa). To add more folders that get CFA protection, use the [ControlledFolderAccessProtectedFolders](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#controlledfolderaccessprotectedfolders) CSP:

**OMA-URI path**: `./Device/Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessProtectedFolders`  
**Value**: Enter one or more folder paths separated by the pipe \(`|`\) character.

For example, `C:\Data\Reports|C:\Data\Finance`.

### Allow apps to modify files in protected folders using the Policy CSP

Use the [ControlledFolderAccessAllowedApplications](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#controlledfolderaccessallowedapplications) CSP to allow more apps to make changes to files in protected folders.

**OMA-URI path**: `./Device/Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessAllowedApplications`  
**Value**: Enter one or more app paths separated by the pipe \(`|`\) character. The path of each app can include environment variables and wildcards, as described in [Allow apps to modify files in protected folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders).

For example, `C:\Apps\app1.exe|%ProgramFiles%\Fabrikam\DriveManager\*\DriveService.exe`

## Configure CFA in Microsoft Configuration Manager

In Microsoft Configuration Manager, you configure CFA in a Windows Defender Exploit Guard policy. For instructions, see the CFA information in [Create and deploy an Exploit Guard policy](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA).

Note

For considerations when you add protected folders or allow apps \(such as wildcard support and the requirement to restart allowed apps\), see [Add other folders to CFA](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#add-other-folders-to-cfa) and [Allow apps to modify files in protected folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders).

## Configure CFA in Group Policy

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Microsoft Defender Exploit Guard** > **Controlled Folder Access**.
5. In the details pane of **Controlled Folder Access**, the available settings are:

   - [Configure allowed applications](#allow-apps-to-modify-files-in-protected-folders-in-group-policy)
   - [Configure controlled folder access](#enable-cfa-in-group-policy)
   - [Configure protected folders](#add-folders-to-protected-folders-in-group-policy)


   To open and configure a CFA setting, use any of the following methods:


   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Microsoft Defender Exploit Guard** > **Controlled Folder Access**.

The available settings are described in the following subsections.

Important

Quotation marks, leading spaces, trailing spaces, and extra characters aren't supported in any of the CFA values in Group Policy.

### Enable CFA in Group Policy

1. In the details pane of **Controlled Folder Access**, open the **Configure controlled folder access** setting.
2. In the setting window that opens, configure the following options:

   1. Select **Enabled**.
   2. **Configure the guard my folders feature**: Select one of the following [mode values](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#modes-for-cfa):

      - **Disable \(Default\)**
      - **Block**
      - **Audit Mode**
      - **Block disk modification only**
      - **Audit disk modification only**


   [![Screenshot shows the group policy option enabled and Audit Mode selected.](https://learn.microsoft.com/en-us/defender-endpoint/media/controlled-folder-access-group-policy-enable.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/controlled-folder-access-group-policy-enable.png#lightbox)

Important

To fully enable CFA, you must set the Group Policy option to **Enabled** and select **Block** in the options drop-down menu.

### Add folders to protected folders in Group Policy

1. In the details pane of **Controlled Folder Access**, open the **Configure protected folders** setting.

   1. Select **Enabled**.
   2. **Enter the folders that should be guarded**: Select **Show...**.
   3. In the setting window that opens, configure the following options:

      - **Value name**: Enter the path to include in CFA protection.
      - **Value**: Enter the value `0`.


   Repeat this step as many times as necessary. When you're finished, select **OK**.


   For considerations when you add folders \(such as support for network shares, mapped drives, and environment variables\), see [Add other folders to CFA](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#add-other-folders-to-cfa).

### Allow apps to modify files in protected folders in Group Policy

1. In the details pane of **Controlled Folder Access**, open the **Configure allowed applications** setting.

   1. Select **Enabled**.
   2. **Enter the applications that should be trusted**: Select **Show...**.
   3. In the setting window that opens, configure the following options:

      - **Value name**: Enter the path and file name of the application that's allowed to make changes to files in protected folders.
      - **Value**: Enter the value `0`.


   Repeat this step as many times as necessary. When you're finished, select **OK**.


   For considerations when you allow apps \(such as wildcard support and the requirement to restart allowed apps\), see [Allow apps to modify files in protected folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders).

## Enable and configure CFA in PowerShell

On the target device, run the commands in this section from an elevated PowerShell session \(a PowerShell window you opened by selecting **Run as administrator**\).

To turn on CFA and select the [protection mode](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#modes-for-cfa), use the following command:

```powershell
Set-MpPreference -EnableControlledFolderAccess <Mode>
```

Valid values for the *EnableControlledFolderAccess* parameter are:

- `0` or `Disabled` \(default\)
- `1` or `Enabled`
- `2` or `AuditMode`
- `3` or `BlockDiskModificationOnly`
- `4` or `AuditDiskModificationOnly`

To see the existing CFA mode on the device, run the following command:

```powershell
Get-MpPreference | Format-Table EnableControlledFolderAccess
```

Note

- In the following subsections, **Set-MpPreference** *overwrites* any existing protected folders or allowed apps with the values you specify. To see the list of existing values, run the following commands in an elevated PowerShell session:

  ```powershell
  $cfa = Get-MpPreference; "ProtectedFolders:"; "-"*25; $cfa.ControlledFolderAccessProtectedFolders | Sort-Object; "`n`n"; "AllowedApplications:"; "-"*25; $cfa.ControlledFolderAccessAllowedApplications | Sort-Object
  ```


  To add other folders or allowed apps to CFA without affecting any existing values, use the **Add-MpPreference** cmdlet. To remove the specified folders or allowed apps from CFA without affecting other existing values, use the **Remove-MpPreference** cmdlet. The command syntax is identical for the three cmdlets.

- The protected folders and allowed apps take effect only when CFA is turned on \(the *EnableControlledFolderAccess* value isn't `0` or `Disabled`\).

### Add folders to protected folders in PowerShell

To [add more folders for CFA to protect](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#add-other-folders-to-cfa), use the following syntax in an elevated PowerShell session:

```powershell
<Add-MpPreference | Set-MpPreference | Remove-MpPreference> -ControlledFolderAccessProtectedFolders "<Path1>","<Path2>",..."<PathN>"
```

The following example adds the specified folders to the existing list of protected folders:

```powershell
Add-MpPreference -ControlledFolderAccessProtectedFolders "C:\Folder1","C:\Folder2"
```

### Allow apps to modify files in protected folders in PowerShell

To add [allowed apps](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders) that can make changes to files in protected folders, use the following syntax in an elevated PowerShell session:

```powershell
<Add-MpPreference | Set-MpPreference | Remove-MpPreference> -ControlledFolderAccessAllowedApplications "<PathAndFilename1>","<PathAndFilename2>",..."<PathAndFilenameN>"
```

The following example replaces any existing allowed apps with the specified apps. The path can include environment variables and wildcards, as described in [Allow apps to modify files in protected folders](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#allow-apps-to-modify-files-in-protected-folders):

```powershell
Set-MpPreference -ControlledFolderAccessAllowedApplications "C:\Apps\app1.exe","%ProgramFiles%\Fabrikam\DriveManager\*\DriveService.exe"
```

## Configure CFA in the Windows Security app

You can use the [Windows Security app](https://support.microsoft.com/Windows/Security/Windows-Security/stay-protected-with-the-windows-security-app) on individual devices to configure CFA. This method is useful for testing or for configuring a single device. To configure CFA on many devices, use one of the enterprise management methods described earlier in this article.

Note

The Windows Security app supports only **On** \(equivalent to the **Enabled** [mode](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#modes-for-cfa)\) and **Off** \(the **Disabled** mode\). To use **Audit Mode** or the disk modification modes, use one of the other methods described in this article.

1. In the **Windows security** app on the device, go to **Virus & threat protection**.
2. In the **Virus & threat protection** pane, in the **Virus & threat protection settings** section, select **Manage settings**.
3. In the **Virus & threat protection** pane, in the **Controlled folder access** section, select **Manage controlled folder access**.
4. In the **Ransomware protection** pane, the following settings are available in the **Controlled folder access** section:

   - [Turn controlled folder access on or off](#enable-cfa-in-the-windows-security-app)
   - [Protected folders](#add-folders-to-protected-folders-in-the-windows-security-app)<sup>\*</sup>
   - [Allow an app through Controlled folder access](#allow-apps-to-modify-files-in-protected-folders-in-the-windows-security-app)<sup>\*</sup>


   <sup>\*</sup> This setting is available only when CFA is turned on.

The available settings are described in the following subsections.

### Enable CFA in the Windows Security app

1. In the **Controlled folder access** section on the **Ransomware protection** pane, slide the toggle to ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **On**.
2. Select **Yes** in the **User Account Control** prompt.

   If you previously specified protected folders and allowed apps before you disabled CFA, you're asked to confirm whether you want to keep those values.

### Add folders to protected folders in the Windows Security app

1. In the **Controlled folder access** section on the **Ransomware protection** pane, select **Protected folders**.
2. Select **Yes** on the **User Account Control** prompt.
3. In the pane that opens, select **+ Add a protected folder**, and then find and select the folder. Repeat this step as many times as necessary.

### Allow apps to modify files in protected folders in the Windows Security app

1. In the **Controlled folder access** section on the **Ransomware protection** pane, select **Allow an app through Controlled folder access**.
2. Select **Yes** on the **User Account Control** prompt.
3. In the **Allow an app through the Controlled folder access** pane, select **+ Add an allowed app**, and then select one of the following values:

   - **Recently blocked apps**: In the **Recently blocked apps** dialog that opens, select an app from the list of recently blocked apps.

     If no recently blocked apps are shown, select **Browse all apps** to find and select the .exe or .com file to add.
   - **Browse all apps**: Find and select the .exe or .com file to add.


   Repeat this step as many times as necessary.

## Related content

- [Controlled folder access \(CFA\) overview](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview)
- [Evaluate Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/evaluate-mde)
