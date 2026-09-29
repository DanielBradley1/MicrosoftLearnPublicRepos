<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-automated-investigations-remediation -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Configure automated investigation and remediation capabilities in Microsoft Defender for Endpoint

If your organization is using [Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) \(or [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview)\), [automated investigation and remediation capabilities](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) can save your security operations team time and effort. As outlined in [Enhance your SOC with Microsoft Defender for Endpoint automatic investigation and remediation](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946), these capabilities mimic the ideal steps that a security analyst takes to investigate and remediate threats. For more information, see [Automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations).

Important

As of September 1, 2026, Automated Investigation and Response \(AIR\) will no longer run as a separate investigation experience or be available for manual triggering in Microsoft Defender.

AIR detection and response capabilities are already included in Microsoft Defender's default antivirus protection stack and run automatically. For on-demand investigations, run a full antivirus scan as needed.

If you're using Defender for Endpoint, you can specify an automation level so that when a threat is detected on a device, the detected threat can be remediated automatically or only upon approval by your security team. You can configure automated investigation and remediation with device groups.

Note

In Defender for Business, automated investigation is configured automatically. See [Review settings for advanced features in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings#review-settings-for-advanced-features).

## Set up device groups

To create device groups and configure automation levels in the Microsoft Defender portal, follow these steps:

1. In the [Microsoft Defender portal](https://security.microsoft.com), on the **Settings** page, under **Permissions**, select **Device groups**.
2. Select **+ Add device group**.
3. Create at least one device group, as follows:

   - Specify a name and description for the device group.
   - In the **Automation level list**, select a level, such as **Full - remediate threats automatically**. The automation level determines whether remediation actions are taken automatically, or only upon approval. To learn more, see [Automation levels in automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels).
   - In the **Members** section, use one or more conditions to identify and include devices.

4. Select **Done** when you're finished setting up your device group.

Note

The **Automated Investigation** option has been removed from the advanced features setting in Defender for Endpoint. Automated investigation is now enabled by default.

## Next steps

- [Visit the Action Center to view pending and completed remediation actions](https://learn.microsoft.com/en-us/defender-endpoint/auto-investigation-action-center#the-unified-action-center)
- [Review and approve pending actions](https://learn.microsoft.com/en-us/defender-endpoint/manage-auto-investigation)

## See also

- [Address false positives/negatives in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives)
- [Automation levels in automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels)
