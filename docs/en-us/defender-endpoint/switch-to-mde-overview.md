<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-overview -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Migrate to Microsoft Defender for Endpoint from non-Microsoft endpoint protection

If you're ready to move from a non-Microsoft endpoint protection solution to [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint), or you're interested in what all is involved in the process, use this article as a guide. This article describes the overall process of moving to [Defender for Endpoint Plan 1 or Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint). The following image depicts the migration process at a high level:

[![Diagram depicting the process of migrating to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/media/nonms-mde-migration.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/nonms-mde-migration.png#lightbox)

When you migrate to Defender for Endpoint, you begin with your non-Microsoft antivirus/antimalware protection in active mode. Then, you configure Microsoft Defender Antivirus in passive mode, and configure Defender for Endpoint features. Then, you onboard your organization's devices, and verify that everything is working correctly. Finally, you remove the non-Microsoft solution from your devices.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## The migration process

[![The MDE migration process](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/migration-phases.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/migration-phases.png#lightbox)

The process of migrating to Defender for Endpoint can be divided into three phases, as described in the following table:

| Phase | Description |
| --- | --- |
| [Prepare for your migration](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1) | During [the **Prepare** phase](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1):  <br>1. Update your organization's devices.  <br>2. Get Defender for Endpoint Plan 1 or Plan 2.  <br>3. Plan roles and permissions for your security team, and grant them access to the Microsoft Defender portal.  <br>4. Configure your device proxy and internet settings to enable communication between your organization's devices and Defender for Endpoint.  <br>5. Get baseline performance data for the devices that are onboarded to Defender for Endpoint. |
| [Set up Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2) | During [the **Setup** phase](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2):  <br>1. Enable/reinstall Microsoft Defender Antivirus, and make sure it's in passive mode on devices.  <br>2. Configure your Defender for Endpoint Plan 1 or Plan 2 capabilities.  <br>3. Add Defender for Endpoint to the exclusion list for your existing solution.  <br>4. Add your existing solution to the exclusion list for Microsoft Defender Antivirus.  <br>5. Set up your device groups, collections, and organizational units. |
| [Onboard to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-3) | During [the **Onboard** phase](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-3):  <br>1. Onboard your devices to Defender for Endpoint.  <br>2. Run a detection test to confirm that onboarding was successful.  <br>3. Confirm that Microsoft Defender Antivirus is running in passive mode.  <br>4. Get updates for Microsoft Defender Antivirus.  <br>5. Uninstall your existing endpoint protection solution.  <br>6. Make sure that Defender for Endpoint working correctly. |

## Next step

- Proceed to [Prepare for your migration](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1).

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
