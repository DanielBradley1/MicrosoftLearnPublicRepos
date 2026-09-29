<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-profiles-approve-sys-extensions-intune -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Approve Microsoft Defender for Endpoint macOS system extensions in Microsoft Intune

Use the Microsoft Intune settings catalog to approve the endpoint security and network extensions required by Microsoft Defender for Endpoint on managed macOS devices.

The procedure in this article requires Microsoft Intune. Intune is a separate product that isn't part of Microsoft Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, see [Configure Microsoft Defender for Endpoint system extension profiles with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-sysext-policies#configure-profiles-with-jamf-pro). For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

Note

The macOS **Extensions** template in Intune was deprecated in the August 2024 service release \(2408\). Policies created with the template continue to work, but you can't create new policies with it.

Use the settings catalog to create policies that configure the macOS System Extensions payload.

## Prerequisites

Before you create the policy, verify the following requirements:

- The devices meet the [Microsoft Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites).
- The devices are enrolled in Intune by using **Automated Device Enrollment** or **Device enrollment**. For more information, see [Enrollment guide: Enroll macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/guide-macos).
- Your account has the Intune **Policy and Profile Manager** role. For more information, see [Built-in roles for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager).

## Configure the Intune system extensions policy

Create a policy by following the instructions in [Create a policy using the settings catalog in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) \(link opens in a new window\).

When you create the policy on the **Policies** tab of the **Devices \| Configuration** page in the Microsoft Intune admin center at [https://intune.microsoft.com/#view/Microsoft\_Intune\_DeviceSettings/DevicesMenu/~/configuration](https://intune.microsoft.com/#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/configuration), by selecting **Create** > ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **New policy**, use these specific settings:

- **Platform**: Select **macOS**.
- **Profile type**: Select **Settings catalog**.

In the **Settings catalog** wizard, add and configure the Defender for Endpoint system extension settings on the **Configuration settings** tab:

1. Select **Add settings**.
2. In the **Settings picker**, enter `allowed system` in the search box, and then select **Search**.
3. Under **Browse by category**, select **System Configuration** > **System Extensions**.
4. Select the following settings:

   - **Allowed System Extension Types**
   - **Allowed System Extensions**


   [![Screenshot of the Intune Settings picker with Allowed System Extension Types and Allowed System Extensions selected.](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-select.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-select.png#lightbox)

5. Close the **Settings picker**.
6. Configure **Allowed System Extensions**:

   1. In the **Allowed System Extensions** section, select **+ Edit instance**.
   2. In the **Configure instance** flyout, enter the following bundle identifiers, one per box:

      - `com.microsoft.wdav.epsext`
      - `com.microsoft.wdav.netext`

   3. For **Team Identifier**, enter `UBF8T346G9`.
   4. Select **Save**.


   [![Screenshot of the Configure instance flyout with the Defender for Endpoint bundle identifiers and team identifier entered.](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-allowed-system-extensions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-allowed-system-extensions.png#lightbox)

7. Configure **Allowed System Extension Types**:

   1. In the **Allowed System Extension Types** section, select **+ Edit instance**.
   2. In the **Configure instance** flyout, enter the following values, one per box:

      - `Network`
      - `EndpointSecurity`

   3. For **Team Identifier**, enter `UBF8T346G9`.
   4. Select **Save**.


   [![Screenshot of the Configure instance flyout with Network, EndpointSecurity, and the Microsoft team identifier entered.](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-allowed-system-extension-types.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-allowed-system-extension-types.png#lightbox)

8. Verify that both entries appear on the **Configuration settings** tab.

   [![Screenshot of the Configuration settings tab with Allowed System Extensions and Allowed System Extension Types configured.](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-configured-settings.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/intune-macos-settings-catalog-configured-settings.png#lightbox)

On the **Assignments** tab, assign the policy to the devices that should receive it. Complete the remaining tabs, and then create the policy.

The next time the targeted devices check in, they receive the system extension settings.
