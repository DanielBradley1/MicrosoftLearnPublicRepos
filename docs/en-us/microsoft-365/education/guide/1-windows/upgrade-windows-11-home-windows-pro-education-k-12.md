<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-windows/upgrade-windows-11-home-windows-pro-education-k-12 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Upgrade Windows 11 Home to Windows 11 Pro Education for K-12

Note

This offer is available to **eligible K-12 education customers only**.

Microsoft is introducing a free upgrade path that enables eligible K-12 education tenants to upgrade devices from **Windows 11 Home** to **Windows 11 Pro Education**. This upgrade path allows organizations to procure devices with Windows 11 Home, upgrade them to Windows 11 Pro Education, and manage them by using school IT administration tools.

The Windows 11 Home to Pro Education upgrade feature is available starting with the June 2026 Cumulative Update \(CD release 2026.06\). To use this feature, devices must be running Windows build 26100.8733 or later and have KB5095093 installed.

**Appropriate roles:** IT Administrator

## Eligibility requirements

To use this upgrade, you must meet all the following requirements.

### Organization eligibility

- K‑12 education institutions only
- IT administrators managing devices in tenants classified as Academic \(K‑12 segment\)
- Organizations using Microsoft Entra ID with a verified academic domain

Note

Higher education \(HED\) and mixed-segment domains aren't eligible.

### User requirements

- You must sign in using a school IT administrator account or a valid K-12 Education customer with Academic Entra AAD domain ID.

Note

Personal Microsoft accounts aren't supported.

## Device requirements

- The device must be running **Windows 11 Home** or **Windows 11 Home N**.

## Network requirements

- The device must be able to reach Microsoft Licensing service at Dls.microsoft.com.

Note

This upgrade is one way ONLY. Reverting to Windows Home isn't supported without a clean OS reinstall.

## Instructions

1. Sign in to the device using a local account.
2. Open **Command Prompt** and run it as **Administrator**.
3. Run the following command:

   ```
   ClipUpgrade.exe
   ```

4. When prompted, confirm that you want to upgrade the device.

   ![Screenshot of Windows upgrade dialog box.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/windows/windows-upgrade.png)
5. Sign in using K-12 organization account to validate eligibility.

   ![Screenshot of sign in dialog box.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/windows/signin.png)
6. The device prepares the upgrade and completes it after a restart.
7. After restarting, verify the upgrade:

   - Go to **Settings** > **System** > **Activation**.
   - Confirm the device shows **Windows 11 Pro Education**.


   ![Screenshot of system activation.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/windows/system-activation.png)

Note

These steps upgrade the device edition only. Separate steps are required to join the device to Microsoft Entra ID \(Azure AD\).

## Support

**Need help?** Contact **Microsoft Support** for assistance.

## Related content

- [Upgrade Windows 11 Home to Windows 11 Education - Partner Center \| Microsoft Learn](https://learn.microsoft.com/en-us/partner-center/customers/upgrade-windows-to-education)
