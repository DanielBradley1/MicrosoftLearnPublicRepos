<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-machines -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Review device configuration in Microsoft Defender for Endpoint

Device configuration management in Microsoft Defender for Endpoint \(MDE\) summarizes how endpoint security settings are managed and highlights gaps in onboarding and protection coverage. Use the dashboard to review your organization's devices and open the appropriate management experiences.

The cards you see depend on your enabled features, integrations, and permissions.

## Review device configuration management

On the **Device configuration management** page in the Microsoft Defender portal at [https://security.microsoft.com/configuration\_management](https://security.microsoft.com/configuration_management), review the available cards:

- **Device security management**: Shows which security configuration management tool is used on devices, grouped by operating system. The data includes endpoints last seen in the past six months.
- **Onboarded via MDE security management**: Shows the onboarding and health status of devices managed through Defender for Endpoint security settings management.
- **Onboarded via Intune**: Compares Intune-managed devices that are onboarded to Defender for Endpoint with devices that aren't onboarded.
- **Attack surface management**: Provides access to attack surface management for devices.
- **Web protection coverage**: Summarizes device coverage for web content filtering policies and custom URL and domain indicators.

Depending on your environment, the page might also show a **Domain Controller Configuration** card.

## Choose a device management method

You can manage Defender security settings on devices enrolled in Intune or on supported devices that aren't enrolled in Intune.

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To enroll and manage devices with Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have an Intune subscription, use Defender for Endpoint security settings management to manage supported devices that aren't enrolled in Intune. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing).

### Enroll devices in Intune

Intune-managed devices receive the policies and profiles you assign in Intune. Choose an enrollment method based on your device ownership and deployment scenario. For guidance, see [Windows device enrollment guide for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/guide).

An Intune license is required for each user or device that benefits from the Intune service. For user-driven enrollment, assign the user an Intune license before enrollment. For instructions, see [Assign Microsoft Intune licenses](https://learn.microsoft.com/en-us/intune/fundamentals/assign-licenses).

To connect the services and onboard devices through Intune, see [Configure Microsoft Defender for Endpoint with Intune and onboard devices](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration).

### Manage devices that aren't enrolled in Intune

Defender for Endpoint security settings management uses Intune endpoint security policies to manage supported devices that are onboarded to Defender for Endpoint but aren't enrolled in Intune. The Defender for Endpoint subscription provides access to the **Endpoint security** area of the Intune admin center for this scenario.

For supported platforms, licensing requirements, and configuration instructions, see [Use Intune to manage Defender settings on devices that aren't enrolled in Intune](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management).

## Get the required permissions

Use a role with the least permissions required for each task:

- **Connect Intune and Defender for Endpoint**: In Intune, use the built-in **Endpoint Security Manager** role or a custom role with **Read** and **Modify** permissions for **Mobile Threat Defense**. In the Defender portal, use the **Security Administrator** role in Microsoft Entra ID or a Defender for Endpoint role with the **Manage security settings in Windows Security Center** permission.
- **Create and assign an endpoint detection and response policy**: Use **Endpoint Security Manager** or a custom Intune role with **Assign**, **Create**, **Delete**, **Read**, **Update**, and **View Reports** permissions for **Endpoint Detection and Response**.
- **Manage security baselines**: Use **Policy and Profile Manager** or a custom Intune role with **Assign**, **Create**, **Delete**, **Read**, and **Update** permissions for **Security baselines** and **Read** permission for **Organization**.

For complete integration requirements, see [Role-based access control prerequisites for Intune and Defender for Endpoint](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview#role-based-access-control).

To create a role with only the permissions your administrators need, see [Create a custom role in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role).

## More information

- [Get devices onboarded to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-onboarding): Track the onboarding status of Intune-managed devices and onboard more devices through Intune.
- [Increase compliance with the Defender for Endpoint security baseline](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline): Create, assign, and monitor the Defender for Endpoint security baseline in Intune.
- [Monitor ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor): Monitor attack surface reduction \(ASR\) rule events by using advanced hunting and the ASR rules report in the [Microsoft Defender portal](https://security.microsoft.com).
