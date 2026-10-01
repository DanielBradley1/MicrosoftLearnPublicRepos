<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-portal-advanced-feature-settings -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Review and edit settings in Microsoft Defender for Business

You can view and edit settings, such as portal settings and advanced features, in the [Microsoft Defender portal](https://security.microsoft.com). Use this article to get an overview of the various settings that are available and how to edit your Defender for Business settings.

## View settings for advanced features

In the [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Endpoints** > **General** > **Advanced features**.

The following table describes advanced feature settings.

| Setting | Description |
| --- | --- |
| **Automated Investigation**  <br>\(turned on by default\) | As alerts are generated, automated investigations can occur. Each automated investigation determines whether a detected threat requires action and then takes or recommends remediation actions. For example:<br><br>- Send a file to quarantine.<br>- Stop a process.<br>- Isolate a device.<br>- Blocking a URL.<br><br>  <br>While an investigation runs, any related alerts that arise are added to the investigation until it finishes. If an affected entity is seen elsewhere, the automated investigation expands its scope to include that entity, and the investigation process repeats.  <br>  <br>You can view investigations on the **Incidents** page. Select an incident, and then select the **Investigations** tab.  <br>  <br>By default, automated investigation and response capabilities are turned on organization wide. *We recommend keeping automated investigation turned on*. If you turn it off, real-time protection in Microsoft Defender Antivirus is affected, and your overall level of protection is reduced.  <br>  <br>[Learn more about automated investigations](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations). |
| **Live Response** | Defender for Business includes the following types of manual response actions:<br><br>- Run antivirus scan<br>- Isolate device<br>- Stop and quarantine a file<br>- Add an indicator to block or allow a file<br><br>  <br>[Learn more about response actions](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts). |
| **Live Response for Servers** | This setting is currently not available in Defender for Business. |
| **Live Response unsigned script execution** | This setting is currently not available in Defender for Business. |
| **Enable EDR in block mode**  <br>\(turned on by default\) | Provides added protection from malicious artifacts when Microsoft Defender Antivirus isn't the primary antivirus product and is running in passive mode on a device. Endpoint detection and response \(EDR\) in block mode works behind the scenes to remediate malicious artifacts detected by EDR capabilities. The primary non-Microsoft antivirus product might miss these artifacts.  <br>  <br>[Learn more about EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode). |
| **Allow or block a file**  <br>\(turned on by default\) | Enables you to allow or block a file by using [indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file). This capability requires Microsoft Defender Antivirus to be in active mode and [cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus) turned on.  <br>  <br>Blocking a file prevents it from being read, written, or executed on devices in your organization.  <br>  <br>[Learn more about indicators for files](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file). |
| **Custom network indicators**  <br>\(turned on by default\) | Enables you to allow or block an IP address, URL, or domain by using [network indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain). This capability requires Microsoft Defender Antivirus to be in active mode and [network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection) turned on.  <br>  <br>You can allow or block IPs, URLs, or domains based on your threat intelligence. You can also prompt users if they open a risky app, but the prompt doesn't stop them from using the app.  <br>  <br>[Learn more about network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection). |
| **Tamper protection**  <br>\(we recommend you turn on this setting\) | Tamper protection prevents malicious apps from doing actions such as:<br><br>- Disable virus and threat protection<br>- Disable real-time protection<br>- Turn off behavior monitoring<br>- Disable cloud protection<br>- Remove security intelligence updates<br>- Disable automatic actions on detected threats<br><br>  <br>Tamper protection essentially locks Microsoft Defender Antivirus to its secure, default values and prevents apps and unauthorized methods from changing your security settings.  <br>  <br>[Learn more about tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview). |
| **Show user details**  <br>\(turned on by default\) | Enables people in your organization to see details, such as user pictures, names, titles, and departments. These details are stored in Microsoft Entra ID.  <br>  <br>[Learn more about user profiles in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-user-profile-info). |
| **Skype for Business integration**  <br>\(turned on by default\) | Integration with Microsoft Teams, or the former Skype for Business, enables one-click communication between people in your business. |
| **Web content filtering**  <br>\(turned on by default\) | Blocks access to websites that contain unwanted content and tracks web activity across all domains. See [Set up web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering). |
| **Microsoft Intune connection**  <br>\(we recommend you turn on this setting if you have Intune\) | If your organization's subscription includes Microsoft Intune \(included in [Microsoft 365 Business Premium resources](https://learn.microsoft.com/en-us/microsoft-365/business-premium/)\), this setting enables Defender for Business to share information about devices with Intune. |
| **Device discovery**  <br>\(turned on by default\) | Enables your security team to find unmanaged devices that are connected to your company network. Unknown and unmanaged devices introduce significant risks to your network, whether it's an unpatched printer, a network device with a weak security configuration, or a server with no security controls.  <br>  <br>Device discovery uses onboarded devices to discover unmanaged devices, so your security team can onboard the unmanaged devices and reduce your vulnerability.  <br>  <br>[Learn more about device discovery](https://learn.microsoft.com/en-us/defender-endpoint/device-discovery). |
| **Preview features** | Microsoft is continually updating services such as Defender for Business to include new feature enhancements and capabilities. If you opt in to receive preview features, you're among the first to try upcoming features in the preview experience.  <br>  <br>[Learn more about preview features](https://learn.microsoft.com/en-us/defender-xdr/preview). |

## View and edit other settings in the Microsoft Defender portal

In addition to security policies applied to devices, you can view and edit other settings in Defender for Business. For example, you can specify the time zone to use, and you can onboard or offboard devices.

Note

You might see more settings in your organization than are listed in this article. This article highlights the most important settings that you should review in Defender for Business.

### Settings to review for Defender for Business

The following table describes settings you can view and edit in Defender for Business:

| Category | Setting | Description |
| --- | --- | --- |
| **Security center** | **Time zone** | Select the time zone to use for the dates and times displayed in incidents, detected threats, and automated investigation and remediation. You can either use UTC or your local time zone \(*recommended*\). |
| **Microsoft Defender XDR** | **Account** | View details such as where your data is stored, your tenant ID, and your organization ID \(org ID\). |
| **Microsoft Defender XDR** | **Preview features** | Turn on preview features to try upcoming features and new capabilities. You can be among the first to preview new features and provide feedback. |
| **Endpoints** | **Email notifications** | Set up or edit your email notification rules. When vulnerabilities are detected or an alert is created, the recipients specified in your email notification rules receive an email notification. [Learn more about email notifications](https://learn.microsoft.com/en-us/defender-business/mdb-email-notifications). |
| **Endpoints** | **Device management** > **Onboarding** | Onboard devices to Defender for Business by using a downloadable script. For more information, see [Onboard devices to Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices). |
| **Endpoints** | **Device management** > **Offboarding** | Offboard \(remove\) devices from Defender for Business. Offboarded devices no longer send data to Defender for Business. Data from when the device was onboarded is retained. For more information, see [Offboarding a device](https://learn.microsoft.com/en-us/defender-business/mdb-offboard-devices). |

### Access your settings in the Microsoft Defender portal

1. Go to the [Microsoft Defender portal](https://security.microsoft.com/), and sign in.
2. Select **Settings**, and then select a category such as **Security center**, **Microsoft Defender XDR**, or **Endpoints**.
3. In the list of settings, select an item to view or edit.

## Next step

[Change your endpoint security subscription](https://learn.microsoft.com/en-us/defender-business/mdb-manage-subscription)
