<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1 -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Migrate to Microsoft Defender for Endpoint - Phase 1: Prepare

Prepare your organization to migrate to Defender for Endpoint by updating devices, confirming licenses, configuring portal access, reviewing connectivity, and capturing baseline performance data before onboarding.

## Phase 1: Prepare

| ![Diagram of migration phases highlighting Phase 1: Prepare as the current step.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/prepare.png#lightbox)  <br>Phase 1: Prepare | [![Diagram of migration phases highlighting Phase 2: Set up.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/setup.png#lightbox)](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2)<br><br>  <br>[Phase 2: Set up](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2) | [![Diagram of migration phases highlighting Phase 3: Onboard.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/onboard.png#lightbox)](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-3)<br><br>  <br>[Phase 3: Onboard](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-3) |
| --- | --- | --- |
| *You're here!* |  |  |

**Welcome to the Prepare phase of [migrating to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-overview#the-migration-process)**.

In this phase, you prepare your environment before you set up and onboard Defender for Endpoint.

This migration phase includes the following steps:

1. Update your organization's devices.
2. Get Microsoft Defender for Endpoint Plan 1 or Plan 2.
3. Grant access to the Microsoft Defender portal.
4. Review device proxy and internet connectivity settings.
5. Capture endpoint performance baseline data.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Step 1: Update your organization's devices

Before migration, update your existing endpoint protection solution, operating systems, and apps. Current software and security updates can help prevent compatibility and deployment problems when you introduce Microsoft Defender Antivirus.

### Update your existing security solution

Install the latest updates for your existing endpoint protection solution. Review your solution provider's documentation for update requirements and procedures.

### Update your organization's devices

Use the following resources to update operating systems:

| OS | Resource |
| --- | --- |
| Windows | [Microsoft Update](https://learn.microsoft.com/en-us/windows/deployment/update/how-windows-update-works) |
| macOS | [How to update the software on your macOS devices](https://support.apple.com/HT201541) |
| iOS | [Update your iPhone, iPad, or iPod touch](https://support.apple.com/HT204204) |
| Android | [Check & update your Android version](https://support.google.com/android/answer/7680439) |
| Linux | [Linux 101: Updating Your System](https://www.linux.com/training-tutorials/linux-101-updating-your-system) |

## Step 2: Get Microsoft Defender for Endpoint Plan 1 or Plan 2

Get Defender for Endpoint, assign the required licenses, and verify that the service is provisioned.

1. Buy or try Defender for Endpoint today. [Start a free trial or request a quote](https://aka.ms/mdatp). For current licensing information, see [Microsoft Defender for Endpoint licensing guidance](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance#microsoft-defender-for-endpoint).
2. Verify that your licenses are provisioned. See [Check your license state](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment#check-your-license-state).
3. Set up your dedicated cloud instance of Defender for Endpoint. See [Defender for Endpoint setup: Tenant configuration](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment#tenant-configuration).
4. If any devices in your organization use a proxy to access the internet, follow the guidance in [Defender for Endpoint setup: Network configuration](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment#network-configuration).

After you provision licenses and configure your Defender for Endpoint organization, grant your security administrators and security operators access to the [Microsoft Defender portal](https://security.microsoft.com).

## Step 3: Grant access to the Microsoft Defender portal

The [Microsoft Defender portal](https://security.microsoft.com) is where you and your security team access and configure features and capabilities of Defender for Endpoint. For an overview of portal features and navigation, see [Overview of the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal).

Use Microsoft Defender unified role-based access control \(RBAC\) to provide centralized, granular permissions to the Microsoft Defender portal.

Important

Starting February 16, 2025, new Microsoft Defender for Endpoint customers have access only to Unified Role-Based Access Control \(URBAC\). Existing customers retain their current roles and permissions. For more information, see [Microsoft Defender unified role-based access control](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

To grant portal access, complete the steps that apply to your organization's permissions model:

1. Plan the roles and permissions for your security administrators and security operators. See [Role-based access control](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment#role-based-access-control).
2. Configure access to the Microsoft Defender portal:

   - If your organization uses unified RBAC, on the **Permissions and roles** page in the Microsoft Defender portal at [https://security.microsoft.com/mtp\_roles](https://security.microsoft.com/mtp_roles), [create custom roles](https://learn.microsoft.com/en-us/defender-xdr/create-custom-rbac-roles), assign the roles to users or Microsoft Entra security groups, and [activate the applicable Defender workloads](https://learn.microsoft.com/en-us/defender-xdr/activate-defender-rbac).
   - If your organization retains the Defender for Endpoint RBAC model, see [Manage portal access using role-based access control](https://learn.microsoft.com/en-us/defender-endpoint/rbac).

## Step 4: Review device proxy and internet connectivity settings

Your devices might require proxy or internet settings to communicate with Defender for Endpoint. Use the following resources for each operating system and subscription:

| Subscription | Operating systems | Resources |
| --- | --- | --- |
| [Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1) | [Windows 11](https://learn.microsoft.com/en-us/windows/whats-new/windows-11-overview)  <br>[Windows 10](https://learn.microsoft.com/en-us/windows/release-health/release-information)  <br>[Windows Server 1803 or later](https://learn.microsoft.com/en-us/windows-server/get-started/whats-new-in-windows-server-1803)  <br>[Windows Server 2016 and later](https://learn.microsoft.com/en-us/windows-server/get-started/whats-new-in-windows-server-2016)\*  <br>[Windows Server 2012 R2](https://learn.microsoft.com/en-us/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)\*  <br>Azure Local nodes running Azure Stack HCI OS, version 23H2 and later | [Configure and validate Microsoft Defender Antivirus network connections](https://learn.microsoft.com/en-us/defender-endpoint/configure-network-connections-microsoft-defender-antivirus) |
| [Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1) | macOS \(see [System requirements](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites)\) | [Defender for Endpoint on macOS: Network connections](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#network-connectivity) |
| [Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1) | Linux \(see [System requirements](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites)\) | [Verify that devices can connect to Defender for Endpoint cloud services](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites#verify-if-devices-can-connect-to-defender-for-endpoint-cloud-services) |
| [Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) | [Windows 11](https://learn.microsoft.com/en-us/windows/whats-new/windows-11-overview)  <br>[Windows 10](https://learn.microsoft.com/en-us/windows/release-health/release-information)  <br>Azure Local nodes running Azure Stack HCI OS, version 23H2 and later  <br>[Windows Server 1803 or later](https://learn.microsoft.com/en-us/windows-server/get-started/whats-new-in-windows-server-1803)  <br>[Windows Server 2016 and later](https://learn.microsoft.com/en-us/windows/release-health/status-windows-10-1607-and-windows-server-2016)  <br>[Windows Server 2012 R2](https://learn.microsoft.com/en-us/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) | [Configure machine proxy and internet connectivity settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet) |
| [Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) | [Windows Server 2008 R2 SP1](https://learn.microsoft.com/en-us/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)  <br>[Windows 8.1](https://learn.microsoft.com/en-us/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)  <br>[Windows 7 SP1](https://learn.microsoft.com/en-us/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) | [Configure proxy and internet connectivity settings](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel#configure-proxy-and-internet-connectivity-settings) |
| [Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) | macOS \(see [System requirements](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)\) | [Defender for Endpoint on macOS: Network connections](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#network-connectivity) |

\* Windows Server 2016 and Windows Server 2012 R2 require the modern unified solution. For more information, see [Onboard Windows Server 2012 R2 and Windows Server 2016 to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server).

Important

The standalone versions of Defender for Endpoint Plan 1 and Plan 2 don't include server licenses. To onboard servers, you need a server license, such as [Microsoft Defender for Servers Plan 1 or Plan 2](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers-select-plan). For more information, see [Defender for Endpoint onboarding Windows Server](https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-server).

## Step 5: Capture endpoint performance baseline data

Before migration, capture baseline performance data from endpoints that will run Defender for Endpoint. Comparing performance before and after onboarding helps you distinguish existing resource usage from changes that might be associated with Microsoft Defender Antivirus.

Collect the process list, aggregate CPU usage, memory usage, and available disk space on all mounted partitions.

Use Windows Performance Monitor \(`perfmon`\) to collect a performance baseline on Windows client devices or Windows Server. For instructions, see [Set up local Performance Monitor on a Windows client or Windows Server](https://learn.microsoft.com/en-us/archive/blogs/yongrhee/setting-a-local-perfmon-in-a-windows-client-or-windows-server).

## Next steps

**Congratulations!** You've completed the **Prepare** phase of [migrating to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-overview#the-migration-process).

- [Proceed to Phase 2: Set up Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2).
