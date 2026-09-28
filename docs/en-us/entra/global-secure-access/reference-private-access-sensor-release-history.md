<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/reference-private-access-sensor-release-history -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Microsoft Entra Private Access Sensor release notes

This article lists the released versions of the Microsoft Entra Private Access Sensor and the changes in each version.

## Download the latest version

You can download the current version of the Private Access Sensor from the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a [Global Secure Access Administrator](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference#global-secure-access-administrator).
2. Browse to **Global Secure Access** > **Connect** > **Connectors and sensors** > **Private access sensors**.
3. Select **Download private access sensor**.

## Version 2.2.42

Released for download on June 16, 2026.

### Security enhancements

- Hardens file and Event Tracing for Windows \(ETW\) channels against tampering by using channel permissions.
- Adds fail-close enforcement for policy failures.

### Kerberos observability

- Adds ticket hash computation for AS-REP, TGS-REQ, and TGS-REP.
- Adds differentiated ETW event IDs for all sensor events.

### Configurable ETW trace file size cap

- Caps ETL, trace, and log files at a configurable maximum size.
- Persists the configured maximum size across upgrades.
- Helps prevent disk exhaustion.

### Diagnostics and telemetry

- Improves telemetry reporting to the cloud.

### Access enforcement

- Adds privileged user access enforcement. This capability restricts cloud-based user access to privileged local users by UPN or SID and is in preview.

### Bug fixes

- Includes bug fixes and minor improvements.
