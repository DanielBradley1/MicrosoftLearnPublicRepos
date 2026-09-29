<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response -->
<!-- Sitemap-Last-Modified: 2026-06-02 -->

# Overview of endpoint detection and response

**Applies to:**

- [Microsoft Defender for Endpoint Plans 1 and 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr)

Endpoint detection and response capabilities in Defender for Endpoint provide advanced attack detections that are near real-time and actionable. Security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats.

When a threat is detected, alerts are created in the system for an analyst to investigate. Alerts with the same attack techniques or attributed to the same attacker are aggregated into an entity called an *incident*. Aggregating alerts in this manner makes it easy for analysts to collectively investigate and respond to threats.

Note

Defender for Endpoint detection is not intended to be an auditing or logging solution that records every operation or activity that happens on a given endpoint. Our sensor has an internal throttling mechanism, so the high rate of repeat identical events don't flood the logs.

Important

[Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1) and [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview) include only the following manual response actions:

- Run antivirus scan
- Isolate device
- Stop and quarantine a file
- Add an indicator to block or allow a file

Inspired by the "assume breach" mindset, Defender for Endpoint continuously collects behavioral cyber telemetry. This includes process information, network activities, deep optics into the kernel and memory manager, user login activities, registry and file system changes, and others. The information is stored for six months, enabling an analyst to travel back in time to the start of an attack. The analyst can then pivot in various views and approach an investigation through multiple vectors.

The response capabilities give you the power to promptly remediate threats by acting on the affected entities.

## Automatic attack disruption

Defender for Endpoint signals contribute to [automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) in Microsoft Defender XDR. Attack disruption uses signal correlation and AI to automatically contain active attacks in progress—such as ransomware, business email compromise, and adversary-in-the-middle attacks—limiting lateral movement and reducing overall impact. Automatic attack disruption works with other Defender XDR sources to contain compromised assets, including automatically disabling compromised user accounts and isolating affected devices.

## See also

- [Incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue)
- [Alerts queue](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue)
- [Devices list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview)
