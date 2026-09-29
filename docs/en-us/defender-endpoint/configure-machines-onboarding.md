<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-onboarding -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Get devices onboarded to Microsoft Defender for Endpoint

Each onboarded device adds an additional endpoint detection and response \(EDR\) sensor and increases visibility over breach activity in your network. Onboarding also ensures that a device can be checked for vulnerable components, for security configuration issues, and can receive critical remediation actions during attacks.

Defender for Endpoint supports [multiple onboarding methods](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy#step-2-select-your-deployment-method). For cloud-native and Intune-managed environments, [Microsoft Intune is the recommended approach](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy#step-1-identify-your-architecture).

Before you begin, review the following prerequisites in the Intune documentation:

- [Review licensing and platform requirements](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-with-intune#prerequisites) for the Intune-Defender integration, including supported platforms and enrollment requirements
- [Ensure you have the necessary permissions](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-integrate#connect-microsoft-defender-for-endpoint-to-intune). The required roles are Endpoint Security Manager in Intune and Security Administrator in Microsoft Entra ID.

## Discover and track unprotected devices

On the **Device configuration management** page in the Microsoft Defender portal at [https://security.microsoft.com/configuration\_management](https://security.microsoft.com/configuration_management), the **Onboarded via Intune** card provides a high-level view of your onboarding rate. The card compares the number of Intune-managed Windows devices onboarded to Defender for Endpoint with the total number of Intune-managed Windows devices.

Note

If you used Configuration Manager, the onboarding script, or other onboarding methods that don't use Intune profiles, you might encounter data discrepancies. To resolve these discrepancies, create a corresponding Intune configuration profile for Defender for Endpoint onboarding and assign that profile to your devices.

## Onboard more devices with Intune policies

Selecting **Onboard more devices** on the card opens the **Endpoint security \| Microsoft Defender for Endpoint** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/atp](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/atp). This page controls the service-to-service connection between Intune and Defender for Endpoint and determines which device platforms participate in the integration. Deploying policies to onboard devices is a separate step done elsewhere in Intune.

To configure this connection and deploy onboarding policies, see [Configure Microsoft Defender for Endpoint with Intune and onboard devices](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-integrate) \(opens in a new tab in the Intune documentation\).

## Related articles

- [Ensure your devices are configured properly](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines)
- [Increase compliance to the Defender for Endpoint security baseline](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline)
- [Monitor ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor)
