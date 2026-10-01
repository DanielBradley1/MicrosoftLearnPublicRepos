<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-requirements -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Microsoft Defender for Business requirements

This article describes the requirements for Defender for Business.

## Review the requirements

The following table lists the basic requirements you need to configure and use Defender for Business.

| Requirement | Description |
| --- | --- |
| Subscription | Microsoft 365 Business Premium or Defender for Business \(standalone\).  <br>For more information, see [How to get Defender for Business](https://learn.microsoft.com/en-us/defender-business/get-defender-business). |
| Datacenter | One of the following datacenter locations:<br><br>- European Union<br>- United Kingdom<br>- United States<br>- Australia |
| User accounts | - User accounts are created in the [Microsoft 365 admin center](https://admin.microsoft.com).<br>- Licenses for Defender for Business or Microsoft 365 Business Premium are assigned in the Microsoft 365 admin center.<br><br>  <br>To get help with this task, see [Add users and assign licenses](https://learn.microsoft.com/en-us/defender-business/mdb-add-users). |
| Permissions | To use the Microsoft Defender portal to view or manage devices and security policies, users must have an appropriate [role assigned in Microsoft Entra ID](https://learn.microsoft.com/en-us/defender-business/mdb-roles-permissions):<br><br>- Security Reader<br>- Security Administrator<br><br>  <br>To learn more, see [Roles and permissions in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-roles-permissions). |
| Browser | Microsoft Edge or Google Chrome |
| Client computer operating system | To manage devices in the Microsoft Defender portal, your devices must run one of the following operating systems:<br><br>- Windows 10 or 11 Business<br>- Windows 10 or 11 Professional<br>- Windows 10 or 11 Enterprise<br>- Mac \(the three most-current releases are supported\)<br><br>  <br>Make sure that [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) is installed on the Windows devices. |
| Mobile devices | To onboard mobile devices, such as iOS or Android OS, you can use [Mobile threat defense capabilities](https://learn.microsoft.com/en-us/defender-business/mdb-mtd) or Microsoft Intune.  <br>  <br>For more information about onboarding devices, including requirements for mobile threat defense, see [Onboard devices to Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices). |
| Server license | To onboard a device running Windows Server or Linux Server, you need another license, such as [Microsoft Defender for Business servers](https://learn.microsoft.com/en-us/defender-business/get-defender-business#how-to-get-microsoft-defender-for-business-servers) \(see note 1 below\). |
| Server requirements | Windows Server endpoints must meet the [requirements for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements#hardware-and-software-requirements), and enforcement scope must be turned on.<br><br>1. In the Microsoft Defender portal, go to **Settings** > **Endpoints** > **Configuration management** > **Enforcement scope**.<br>2. Select **Use MDE to enforce security configuration settings from MEM**, select **Windows Server**.<br>3. Select **Save**.<br><br>  <br>Linux Server endpoints must meet the [prerequisites for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux#prerequisites). |

Note

1. To onboard servers, we recommend using [Microsoft Defender for Business servers](https://learn.microsoft.com/en-us/defender-business/get-defender-business#how-to-get-microsoft-defender-for-business-servers). Alternately, you could use [Microsoft Defender for Servers Plan 1 or Plan 2](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers). For more information, see [Onboard devices to Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices).
2. [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra) manages user permissions and device groups. Microsoft Entra ID is included in your Defender for Business subscription.

   - If you don't have a Microsoft 365 subscription before you start your trial, Microsoft Entra ID is provisioned for you during the activation process.
   - If you do have another Microsoft 365 subscription when you start your Defender for Business trial, you can use your existing Microsoft Entra service.

3. Security defaults are included in Defender for Business. If you prefer to use Conditional Access policies instead, you need Microsoft Entra ID P1 or P2. P1 is included in [Microsoft 365 Business Premium](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-overview). For more information, see [Multifactor authentication in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365).

## Related content

- [Get and provision Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/get-defender-business)
- [Trial user guide: Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/trial-playbook-defender-business)
- [Set up and configure Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-setup-configuration)
