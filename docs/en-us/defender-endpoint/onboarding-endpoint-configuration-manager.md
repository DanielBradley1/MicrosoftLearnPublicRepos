<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/onboarding-endpoint-configuration-manager -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Onboarding using Microsoft Configuration Manager

This article acts as an example onboarding method.

In the [Planning](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy) article, there were several methods provided to onboard devices to the service. This article covers the co-management architecture.

[![The cloud-native architecture](https://learn.microsoft.com/en-us/defender-endpoint/media/co-management-architecture.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/co-management-architecture.png#lightbox) *Diagram of environment architectures*

While Defender for Endpoint supports onboarding of various endpoints and tools, this article doesn't cover them. For information on general onboarding using other supported deployment tools and methods, see [Onboarding overview](https://learn.microsoft.com/en-us/defender-endpoint/onboarding).

This article guides users in:

- Step 1: Onboarding Windows devices to the service
- Step 2: Configuring Defender for Endpoint capabilities

This onboarding guidance walks you through the following basic steps that you need to take when using Microsoft Configuration Manager:

- **Creating a collection in Microsoft Configuration Manager**
- **Configuring Microsoft Defender for Endpoint capabilities using Microsoft Configuration Manager**

Note

Only Windows devices are covered in this example deployment.

## Step 1: Onboard Windows devices using Microsoft Configuration Manager

### Collection creation

To onboard Windows devices with Microsoft Configuration Manager, the deployment can target an existing collection or a new collection can be created for testing.

Onboarding using tools such as Group policy or manual method doesn't install any agent on the system.

Within the Microsoft Configuration Manager, console the onboarding process will be configured as part of the compliance settings within the console.

Any system that receives this required configuration maintains that configuration for as long as the Configuration Manager client continues to receive this policy from the management point.

Follow the steps below to onboard endpoints using Microsoft Configuration Manager.

1. In Microsoft Configuration Manager console, navigate to **Assets and Compliance > Overview > Device Collections**.

   [![The Microsoft Configuration Manager wizard1](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-device-collections.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-device-collections.png#lightbox)
2. Right select **Device Collection** and select **Create Device Collection**.

   [![The Microsoft Configuration Manager wizard2](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-create-device-collection.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-create-device-collection.png#lightbox)
3. Provide a **Name** and **Limiting Collection**, then select **Next**.

   [![The Microsoft Configuration Manager wizard3](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-limiting-collection.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-limiting-collection.png#lightbox)
4. Select **Add Rule** and choose **Query Rule**.

   [![The Microsoft Configuration Manager wizard4](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-query-rule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-query-rule.png#lightbox)
5. Select **Next** on the **Direct Membership Wizard** and select on **Edit Query Statement**.  [![The Microsoft Configuration Manager wizard5](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-direct-membership.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-direct-membership.png#lightbox)
6. Select **Criteria** and then choose the star icon.

   [![The Microsoft Configuration Manager wizard6](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-criteria.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-criteria.png#lightbox)
7. Keep criterion type as **simple value**, choose whereas **Operating System - build number**, operator as **is greater than or equal to** and value **14393** and select on **OK**.  [![The Microsoft Configuration Manager wizard7](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-simple-value.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-simple-value.png#lightbox)
8. Select **Next** and **Close**.

   [![The Microsoft Configuration Manager wizard8](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-membership-rules.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-membership-rules.png#lightbox)
9. Select **Next**.

   [![The Microsoft Configuration Manager wizard9](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-confirm.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-confirm.png#lightbox)

After completing this task, you now have a device collection with all the Windows endpoints in the environment.

## Step 2: Configure Microsoft Defender for Endpoint capabilities

This section guides you in configuring the following capabilities using Microsoft Configuration Manager on Windows devices:

- [**Endpoint detection and response**](#endpoint-detection-and-response)
- [**Next-generation protection**](#next-generation-protection)
- [**Attack surface reduction**](#attack-surface-reduction)

### Endpoint detection and response

#### Windows 10 and Windows 11

From within the Microsoft Defender portal it's possible to download the `.onboarding` policy that can be used to create the policy in System Center Configuration Manager and deploy that policy to Windows 10 and Windows 11 devices.

1. In the [Microsoft Defender portal](https://security.microsoft.com), select [Settings and then Onboarding](https://security.microsoft.com/preferences2/onboarding).
2. Under Deployment method, select the supported version of **Microsoft Configuration Manager**.

   [![The Microsoft Configuration Manager wizard10](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-onboarding-wizard.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-onboarding-wizard.png#lightbox)
3. Select **Download package**.

   [![The Microsoft Configuration Manager wizard11](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-download-package.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-download-package.png#lightbox)
4. Save the package to an accessible location.
5. In Microsoft Configuration Manager, navigate to: **Assets and Compliance > Overview > Endpoint Protection > Microsoft Defender ATP Policies**.
6. Right-click **Microsoft Defender ATP Policies** and select **Create Microsoft Defender ATP Policy**.

   [![The Microsoft Configuration Manager wizard12](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-create-policy.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-create-policy.png#lightbox)
7. Enter the name and description, verify **Onboarding** is selected, then select **Next**.

   [![The Microsoft Configuration Manager wizard13](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-policy-name.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-policy-name.png#lightbox)
8. Select **Browse**.
9. Navigate to the location of the downloaded file from step 4 above.
10. Select **Next**.
11. Configure the Agent with the appropriate samples \(**None** or **All file types**\).

    [![The configuration settings1](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-config-settings.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-config-settings.png#lightbox)
12. Select the appropriate telemetry \(**Normal** or **Expedited**\) then select **Next**.

    [![The configuration settings2](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-telemetry.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-telemetry.png#lightbox)
13. Verify the configuration, then select **Next**.

    [![The configuration settings3](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-verify-configuration.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-verify-configuration.png#lightbox)
14. Select **Close** when the Wizard completes.
15. In the Microsoft Configuration Manager console, right-click the Defender for Endpoint policy you created and select **Deploy**.

    [![The configuration settings4](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-deploy.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-deploy.png#lightbox)
16. On the right panel, select the previously created collection and select **OK**.

    [![The configuration settings5](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-select-collection.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-select-collection.png#lightbox)

#### Previous versions of Windows Client \(Windows 7 and Windows 8.1\)

Follow the steps below to identify the Defender for Endpoint Workspace ID and Workspace Key that will be required for the onboarding of previous versions of Windows.

1. In the [Microsoft Defender portal](https://security.microsoft.com), select **Settings** > **Endpoints** > **Onboarding** \(under **Device Management**\).
2. Under operating system, choose **Windows 7 SP1 and 8.1**.
3. Copy the **Workspace ID** and **Workspace Key** and save them. They'll be used later in the process.

   [![The onboarding process](https://learn.microsoft.com/en-us/defender-endpoint/media/91b738e4b97c4272fd6d438d8c2d5269.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/91b738e4b97c4272fd6d438d8c2d5269.png#lightbox)
4. Install the Microsoft Monitoring Agent \(MMA\).

   MMA is currently \(as of January 2019\) supported on the following Windows Operating Systems:

   - Server SKUs: Windows Server 2008 SP1 or Newer
   - Client SKUs: Windows 7 SP1 and later


   The MMA agent needs to be installed on Windows devices. To install the agent, some systems need to download the [Update for customer experience and diagnostic telemetry](https://support.microsoft.com/servicing/os/windows/2019/11/update-for-customer-experience-and-diagnostic-telemetry) in order to collect the data with MMA. These system versions include but may not be limited to:


   - Windows 8.1
   - Windows 7
   - Windows Server 2016
   - Windows Server 2012 R2
   - Windows Server 2008 R2


   Specifically, for Windows 7 SP1, the following patches must be installed:


   - Install [KB4074598](https://support.microsoft.com/servicing/os/windows-7/2018/02/february-13-2018-kb4074598-monthly-rollup)
   - Install either [.NET Framework 4.5 or later](https://learn.microsoft.com/en-us/dotnet/framework/install/guide-for-developers) **or** [KB3154518](https://support.microsoft.com/topic/support-for-tls-system-default-versions-included-in-the-net-framework-3-5-1-on-windows-7-sp1-and-server-2008-r2-sp1-5ef38dda-8e6c-65dc-c395-62d2df58715a). Do not install both on the same system.

5. If you're using a proxy to connect to the Internet see the Configure proxy settings section.

Once completed, you should see onboarded endpoints in the portal within an hour.

### Next generation protection

Microsoft Defender Antivirus is a built-in anti-malware solution that provides next generation protection for desktops, portable computers, and servers.

1. In the Microsoft Configuration Manager console, navigate to **Assets and Compliance > Overview > Endpoint Protection > Antimalware Polices** and choose **Create Antimalware Policy**.

   [![The antimalware policy](https://learn.microsoft.com/en-us/defender-endpoint/media/9736e0358e86bc778ce1bd4c516adb8b.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/9736e0358e86bc778ce1bd4c516adb8b.png#lightbox)
2. Select **Scheduled scans**, **Scan settings**, **Default actions**, **Real-time protection**, **Exclusion settings**, **Advanced**, **Threat overrides**, **Cloud Protection Service** and **Security intelligence updates** and choose **OK**.

   [![The next-generation protection pane1](https://learn.microsoft.com/en-us/defender-endpoint/media/1566ad81bae3d714cc9e0d47575a8cbd.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/1566ad81bae3d714cc9e0d47575a8cbd.png#lightbox)

   In certain industries or some select enterprise customers might have specific needs on how Antivirus is configured.

   [Quick scan versus full scan and custom scan](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans#comparing-the-quick-scan-full-scan-and-custom-scan)

   For more information, see [Windows Security configuration framework](https://github.com/microsoft/SecCon-Framework/blob/master/windows-security-configuration-framework.md).

   [![The next-generation protection pane2](https://learn.microsoft.com/en-us/defender-endpoint/media/cd7daeb392ad5a36f2d3a15d650f1e96.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/cd7daeb392ad5a36f2d3a15d650f1e96.png#lightbox)

   [![The next-generation protection pane3](https://learn.microsoft.com/en-us/defender-endpoint/media/36c7c2ed737f2f4b54918a4f20791d4b.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/36c7c2ed737f2f4b54918a4f20791d4b.png#lightbox)

   [![The next-generation protection pane4](https://learn.microsoft.com/en-us/defender-endpoint/media/a28afc02c1940d5220b233640364970c.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/a28afc02c1940d5220b233640364970c.png#lightbox)

   [![The next-generation protection pane5](https://learn.microsoft.com/en-us/defender-endpoint/media/5420a8790c550f39f189830775a6d4c9.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/5420a8790c550f39f189830775a6d4c9.png#lightbox)

   [![The next-generation protection pane6](https://learn.microsoft.com/en-us/defender-endpoint/media/33f08a38f2f4dd12a364f8eac95e8c6b.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/33f08a38f2f4dd12a364f8eac95e8c6b.png#lightbox)

   [![The next-generation protection pane7](https://learn.microsoft.com/en-us/defender-endpoint/media/41b9a023bc96364062c2041a8f5c344e.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/41b9a023bc96364062c2041a8f5c344e.png#lightbox)

   [![The next-generation protection pane8](https://learn.microsoft.com/en-us/defender-endpoint/media/945c9c5d66797037c3caeaa5c19f135c.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/945c9c5d66797037c3caeaa5c19f135c.png#lightbox)

   [![The next-generation protection pane9](https://learn.microsoft.com/en-us/defender-endpoint/media/3876ca687391bfc0ce215d221c683970.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/3876ca687391bfc0ce215d221c683970.png#lightbox)
3. Right-click on the newly created anti-malware policy and select **Deploy**.

   [![The next-generation protection pane10](https://learn.microsoft.com/en-us/defender-endpoint/media/f5508317cd8c7870627cb4726acd5f3d.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/f5508317cd8c7870627cb4726acd5f3d.png#lightbox)
4. Target the new anti-malware policy to your Windows collection and select **OK**.

   [![The next-generation protection pane11](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-select-collection.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/configmgr-select-collection.png#lightbox)

After completing this task, you now have successfully configured Microsoft Defender Antivirus.

### Attack surface reduction

The attack surface reduction pillar of Defender for Endpoint includes the feature set that is available under Exploit Guard. Attack surface reduction \(ASR\) rules, Controlled Folder Access, Network Protection, and Exploit Protection.

All these features provide a test mode and a block mode. In test mode, there's no end-user impact. All it does is collect other telemetry and make it available in the Microsoft Defender portal. The goal with a deployment is to step-by-step move security controls into block mode.

To set attack surface reduction rules in test mode:

1. In the Microsoft Configuration Manager console, navigate to **Assets and Compliance > Overview > Endpoint Protection > Windows Defender Exploit Guard** and choose **Create Exploit Guard Policy**.

   [![The Microsoft Configuration Manager console0](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png#lightbox)
2. Select **Attack Surface Reduction**.
3. Set rules to **Audit** and select **Next**.

   [![The Microsoft Configuration Manager console1](https://learn.microsoft.com/en-us/defender-endpoint/media/d18e40c9e60aecf1f9a93065cb7567bd.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/d18e40c9e60aecf1f9a93065cb7567bd.png#lightbox)
4. Confirm the new Exploit Guard policy by selecting **Next**.

   [![The Microsoft Configuration Manager console2](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png#lightbox)
5. Once the policy is created select **Close**.

   [![The Microsoft Configuration Manager console3](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png#lightbox)
6. Right-click on the newly created policy and choose **Deploy**.

   [![The Microsoft Configuration Manager console4](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png#lightbox)
7. Target the policy to the newly created Windows collection and select **OK**.

   [![The Microsoft Configuration Manager console5](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png#lightbox)

After completing this task, you now have successfully configured attack surface reduction rules in test mode.

Below are more steps to verify whether attack surface reduction rules are correctly applied to endpoints. \(This may take few minutes\)

1. From a web browser, go to [Microsoft Defender XDR](https://go.microsoft.com/fwlink/p/?linkid=2077139).
2. Select **Configuration management** from left side menu.
3. Select **Go to attack surface management** in the Attack surface management panel.

   [![The attack surface management](https://learn.microsoft.com/en-us/defender-endpoint/media/security-center-attack-surface-mgnt-tile.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/security-center-attack-surface-mgnt-tile.png#lightbox)
4. Select **Configuration** tab in Attack surface reduction rules reports. It shows attack surface reduction rules configuration overview and attack surface reduction rules status on each device.

   [![The attack surface reduction rules reports1](https://learn.microsoft.com/en-us/defender-endpoint/media/f91f406e6e0aae197a947d3b0e8b2d0d.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/f91f406e6e0aae197a947d3b0e8b2d0d.png#lightbox)
5. Select each device shows configuration details of attack surface reduction rules.

   [![The attack surface reduction rules reports2](https://learn.microsoft.com/en-us/defender-endpoint/media/24bfb16ed561cbb468bd8ce51130ca9d.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/24bfb16ed561cbb468bd8ce51130ca9d.png#lightbox)

See [Monitor ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor) for more details.

#### Set Network Protection rules in test mode

1. In the Microsoft Configuration Manager console, navigate to **Assets and Compliance > Overview > Endpoint Protection > Windows Defender Exploit Guard** and choose **Create Exploit Guard Policy**.

   [![The System Center Configuration Manager1](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png#lightbox)
2. Select **Network protection**.
3. Set the setting to **Audit** and select **Next**.

   [![The System Center Configuration Manager2](https://learn.microsoft.com/en-us/defender-endpoint/media/c039b2e05dba1ade6fb4512456380c9f.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/c039b2e05dba1ade6fb4512456380c9f.png#lightbox)
4. Confirm the new Exploit Guard Policy by selecting **Next**.  [![The Exploit Guard policy1](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png#lightbox)
5. Once the policy is created select on **Close**.

   [![The Exploit Guard policy2](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png#lightbox)
6. Right-click on the newly created policy and choose **Deploy**.  [![The Microsoft Configuration Manager-1](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png#lightbox)
7. Select the policy to the newly created Windows collection and choose **OK**.

   [![The Microsoft Configuration Manager-2](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png#lightbox)

After completing this task, you now have successfully configured Network Protection in test mode.

#### To set Controlled Folder Access rules in test mode

1. In the Microsoft Configuration Manager console, navigate to **Assets and Compliance** > **Overview** > **Endpoint Protection** > **Windows Defender Exploit Guard** and then choose **Create Exploit Guard Policy**.

   [![The Microsoft Configuration Manager-3](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/728c10ef26042bbdbcd270b6343f1a8a.png#lightbox)
2. Select **Controlled folder access**.
3. Set the configuration to **Audit** and select **Next**.

   [![The Microsoft Configuration Manager-4](https://learn.microsoft.com/en-us/defender-endpoint/media/a8b934dab2dbba289cf64fe30e0e8aa4.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/a8b934dab2dbba289cf64fe30e0e8aa4.png#lightbox)
4. Confirm the new Exploit Guard Policy by selecting **Next**.  [![The Microsoft Configuration Manager-5](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0a6536f2c4024c08709cac8fcf800060.png#lightbox)
5. Once the policy is created select on **Close**.

   [![The Microsoft Configuration Manager-6](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/95d23a07c2c8bc79176788f28cef7557.png#lightbox)
6. Right-click on the newly created policy and choose **Deploy**.  [![The Microsoft Configuration Manager-7](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/8999dd697e3b495c04eb911f8b68a1ef.png#lightbox)
7. Target the policy to the newly created Windows collection and select **OK**.

[![The Microsoft Configuration Manager-8](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/0ccfe3e803be4b56c668b220b51da7f7.png#lightbox)

You have now successfully configured Controlled folder access in test mode.

## Related article

- [Onboard Windows devices to Microsoft Defender for Endpoint using Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/onboarding-endpoint-manager)
