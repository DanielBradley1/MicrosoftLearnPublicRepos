<!-- Source: https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Enable Windows diagnostic data and license verification

Some Microsoft Intune features require access to Windows diagnostic data or verification that the tenant owns eligible Windows licenses. Configure these requirements at the tenant level so dependent features can function correctly.

## Enable Windows diagnostic data

To allow Intune to access Windows diagnostic data collected from enrolled devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** > **Connectors and tokens** > **Windows data**.
2. Toggle **Enable features that require Windows diagnostic data in processor configuration** to **On**. The default is *Off*.

Note

There are multiple ways to enable Windows diagnostic data for a tenant. This toggle reflects only your configuration choice for **Intune features**.

Turning this setting **Off** disables Intune features that rely on this configuration, but it might not disable processor configuration that was enabled by other methods.

Features that require Windows diagnostic data include:

- [Compatibility reports for Windows updates](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility)
- [Reports for expedite policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-expedite-policy#monitoring-and-reporting)
- Driver update policies with alerts for Windows driver update failures
- Expedited quality update policies with alerts for Windows expedited update failures
- Feature update policies with alerts for feature update failures

To learn more about this configuration, see [Enable Windows diagnostic data processor configuration](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enable-windows-diagnostic-data-processor-configuration) in the Windows privacy documentation.

## Enable Windows license verification

Some Intune features require an attestation that your tenant owns eligible Windows licenses. This setting confirms tenant entitlement for those features; it does not validate or assign licenses to individual devices.

To attest ownership of the required Windows licenses:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://intune.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/TenantAdminMenu) > [**Connectors and tokens**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens) > \[**Windows data**\].
2. Toggle **I confirm that my tenant owns one of these licenses** to **On**. By default, it's *Off*.

Supported licenses:

- Windows Enterprise E3/E5 or Microsoft 365 F3/E3/E5
- Windows Education A3/A5 or Microsoft 365 A3/A5
- Windows Virtual Desktop Access E3/E5

Features that require license verification include:

- [Compatibility reports for Windows updates](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility)
- [Remediations](https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations)

## Next steps

To understand how Windows diagnostic data is collected and managed, see [Configure Windows diagnostic data in your organization](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization) in the Windows privacy documentation.
