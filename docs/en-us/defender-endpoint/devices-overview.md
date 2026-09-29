<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/devices-overview -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Devices in Microsoft Defender for Endpoint

Devices are the foundation of your security operations in Microsoft Defender for Endpoint. Understanding how devices appear in your environment, how to manage them effectively, and how to organize them for security actions is essential for protecting your organization.

## What are devices in Defender for Endpoint?

Devices in Microsoft Defender for Endpoint include any endpoint that reports security telemetry to the service. This includes:

- **Computers and mobile devices**: Workstations, servers, laptops, and mobile devices \(Windows, macOS, Linux, iOS, Android\)
- **Network devices**: Routers, switches, and other network infrastructure
- **IoT/OT devices**: Printers, cameras, industrial control systems, and operational technology devices

Devices appear in your inventory through two primary methods:

- **Onboarding**: Devices you explicitly onboard to Defender for Endpoint with the full agent installed. Onboarded devices show an **Onboarding status** of **Onboarded** and typically have an **Active** sensor health state. Because the agent is installed, Defender for Endpoint can collect detailed security data from these devices, including alerts, vulnerabilities, and software inventory. For more information, see [Onboard devices to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboarding).
- **Discovery**: Devices automatically discovered on your network without an agent installed. Discovery happens through onboarded endpoints that observe network traffic \(basic discovery\) or actively probe the environment \(standard discovery\). Discovered devices show an **Onboarding status** of **Can be onboarded**, **Unsupported**, or **Insufficient info**. For more information, see [Device discovery overview](https://learn.microsoft.com/en-us/defender-endpoint/device-discovery).
- **IoT and OT devices**: IoT and operational technology \(OT\) devices — such as printers, cameras, and industrial control systems — appear in the inventory when you enable [Microsoft Defender for IoT in the Defender portal](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot). These devices appear on the **IoT/OT devices** tab and include extra fields like device type, subtype, vendor, and model.

The **Discovery sources** column in the [device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview) tells you how each device was found: **MDE** \(found by the Defender for Endpoint sensor\), **Microsoft Defender for IoT** \(discovered by Defender for IoT\), and other sources. Use this column to understand why a device appears and whether it requires onboarding.

## The device lifecycle and journey

Managing devices in Defender for Endpoint follows a predictable lifecycle. The following table outlines the key stages, tasks, roles involved, and related documentation:

| Stage | Tasks | Roles involved | Learn more |
| --- | --- | --- | --- |
| **Discover and onboard devices** | • Discover devices on your network  <br>• Onboard devices with the Defender for Endpoint agent  <br>• View devices in the device inventory  <br>• Assess risk levels and exposure scores | Security Administrator  <br>IT Operations | [Explore devices in the device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview)  <br>[Onboard devices](https://learn.microsoft.com/en-us/defender-endpoint/onboarding)  <br>[Configure device discovery](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-discovery) |
| **Manage scope and relevance** | • Filter out transient devices \(automatic\)  <br>• Exclude devices from vulnerability management \(manual\)  <br>• Determine which devices require security attention | Security Administrator | [Manage device scope and relevance](https://learn.microsoft.com/en-us/defender-endpoint/manage-device-scope-relevance) |
| **Classify and organize with tags and exclusions** | • Add manual tags to individual devices  <br>• Create dynamic tags using rules  <br>• Organize devices into meaningful groups  <br>• Apply tags for business context | Security Administrator  <br>Security Analyst | [Create and manage device tags](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags) |
| **Target devices for security actions** | • Use device groups for role-based access  <br>• Collect custom telemetry from device groups  <br>• Apply automation rules to tagged devices  <br>• Deploy security policies to device groups | Security Administrator  <br>Security Analyst | [Create and manage device tags and target devices](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags)  <br>[Custom data collection](https://learn.microsoft.com/en-us/defender-endpoint/custom-data-collection) |
| **Investigate devices** | • Review device timelines  <br>• Investigate alerts and incidents  <br>• Identify internet-facing devices  <br>• Hunt for threats across device groups  <br>• Take response actions | Security Analyst  <br>Security Administrator | [Investigate devices](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines)  <br>[Review device timeline](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines#investigate-device-timeline)  <br>[Identify internet-facing devices](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines#investigate-internet-facing-devices) |
| **Monitor and maintain** | • Monitor device health status  <br>• Fix unhealthy sensors  <br>• Review sensor health reports  <br>• Track onboarding status | IT Operations  <br>Security Administrator | [Fix unhealthy sensors](https://learn.microsoft.com/en-us/defender-endpoint/fix-unhealthy-sensors)  <br>[Device health reports](https://learn.microsoft.com/en-us/defender-endpoint/device-health-microsoft-defender-antivirus-health) |

## Device targeting

Device targeting uses device tags to identify which devices should receive specific security actions. Rather than managing devices individually, targeting lets you organize devices into meaningful groups and apply configurations, policies, or data collection rules at scale.

### Tags vs. groups

**Device tags** are labels you attach to devices — either manually or through dynamic rules — to capture business context such as department, location, or criticality. All users can see tagged devices. Tags alone don't control access or apply security policies; they provide the organizational foundation for targeting.

**Device groups** build on tags to control which security teams can access and manage specific devices. When you create a device group, you define matching rules \(often based on tags\), set automated remediation levels, and assign Microsoft Entra user groups. Device groups enable role-based access control \(RBAC\) so that, for example, a regional security team sees only devices in their geography. For detailed instructions, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

### Dynamic tags vs. manual tags

**Manual tags** are custom labels you apply directly to individual devices through the portal or API. They're quick to set up and useful for ad-hoc needs like tagging devices during an active investigation. However, they don't scale well and require manual updates. Manual tags aren't supported for custom data collection or some automation scenarios.

**Dynamic tags** are applied automatically based on rules you define in [Asset Rule Management](https://learn.microsoft.com/en-us/defender-xdr/configure-asset-rules). They update as device properties change \(approximately every hour\), scale to thousands of devices, and are required for advanced capabilities like [custom data collection](https://learn.microsoft.com/en-us/defender-endpoint/custom-data-collection). Use dynamic tags whenever you need tags to stay current without manual effort.

Important

Many advanced Defender for Endpoint capabilities, including custom data collection, require dynamic tags. Manual tags aren't supported for these scenarios.

### Targeting scenarios

The following table summarizes common scenarios where device targeting drives security operations.

| Scenario | Approach | Example |
| --- | --- | --- |
| **Scope investigations** | Tag devices by department or incident, then filter alerts and advanced hunting queries by tag. | Investigate all `Finance-Department` devices for suspicious lateral movement. |
| **Collect specialized telemetry** | Create dynamic tags for target devices, then create custom data collection rules. Requires dynamic tags and a Microsoft Sentinel workspace. | Collect file access events from `Database-Servers` to monitor data access. |
| **Automate response actions** | Define automated responses for device groups based on tags. | Auto-isolate `Public-Kiosk` devices when high-severity malware is detected. |
| **Control analyst access \(RBAC\)** | Create device groups from tags and assign them to Microsoft Entra security teams. | Give the Finance Security Team access only to `Finance-Department` devices. |
| **Deploy ASR rules by device type** | Apply different attack surface reduction policies to different tag-based groups. | Aggressive blocking on `Internet-Facing-Servers`; test mode on `Development-Machines`. |
| **Enforce Conditional Access** | Use device risk levels and group membership to inform access decisions. | Require MFA for `High-Risk-Devices` accessing sensitive applications. |
| **Organize by geography** | Tag devices by region or site for distributed security operations. | EMEA security team monitors and responds to `Location-EMEA` devices. |
| **Manage device lifecycle** | Tag devices by operational stage \(Production, Staging, Decommissioning\). | Apply full controls to Production; reduced monitoring for Decommissioning. |
| **Pilot new security features** | Apply manual tags to a pilot group, deploy the feature in test mode, then expand. | Tag 20 devices with `ASR-Pilot-2026`, test new rule, refine, then roll out broadly. |

For step-by-step instructions on creating tags and device groups, see [Create and manage device tags and target devices](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags).

### Security actions powered by targeting

Device tags and groups enable you to apply security operations across multiple areas:

| Security action | Description | Scenarios | Learn more |
| --- | --- | --- | --- |
| **Investigations and threat hunting** | Filter alerts and scope investigations to specific device groups | • Investigate all "Finance-Department" devices for suspicious activity  <br>• Hunt for threats across "Windows-Servers" in a specific region  <br>• Track devices involved in a compromise using incident tags | [Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) |
| **Custom data collection** | Collect specialized telemetry from devices with dynamic tags | • Collect file events from "Database-Servers"  <br>• Capture network connections from "Developer-Workstations"  <br>• Monitor script execution on "Administrative-Systems" | [Custom data collection](https://learn.microsoft.com/en-us/defender-endpoint/custom-data-collection)  <br>[Create custom data collection rules](https://learn.microsoft.com/en-us/defender-endpoint/create-custom-data-collection-rules) |
| **Automation rules** | Apply automated response actions to device categories | • Auto-isolate "Public-Kiosk" devices if malware is detected  <br>• Run forensic collection on "Critical-Servers" during incidents  <br>• Restrict "BYOD-Devices" from sensitive resources | [Automated investigation and response](https://learn.microsoft.com/en-us/defender-xdr/m365d-configure-auto-investigation-response) |
| **Device groups for role-based access** | Control which security analysts can see and act on specific devices | • Finance Security Team manages only "Finance-Department" devices  <br>• Regional teams manage devices in their geographic locations  <br>• Junior analysts access only "Non-Production" device groups | [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups) |
| **Attack surface reduction rules** | Deploy different security controls to different device types | • Strict blocking rules on "Internet-Facing-Servers"  <br>• Test mode on "Development-Machines"  <br>• Standard baseline for general user workstations | [Attack surface reduction rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment) |
| **Conditional Access policies** | Enforce access controls based on device security posture and tags | • Require MFA for "High-Risk-Devices"  <br>• Block "Non-Compliant-Devices" from corporate resources  <br>• Allow "Managed-BYOD" limited access to approved services | [Conditional Access with Intune](https://learn.microsoft.com/en-us/mem/intune/protect/advanced-threat-protection) |
