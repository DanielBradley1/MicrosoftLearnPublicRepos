<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-seenby-function -->
<!-- Sitemap-Last-Modified: 2025-08-05 -->

# SeenBy\(\)

The `SeenBy()` function is invoked to see a list of onboarded devices that have seen a certain device using the device discovery feature.

This function returns a table that has the following column:

| Column | Data type | Description |
| --- | --- | --- |
| `DeviceId` | `string` | Unique identifier for the device in the service |

You can enter up to 1,000 devices in this function.

## Syntax

```kusto
invoke SeenBy(x)
```

- where **x** is the device ID of interest

Tip

Enrichment functions show supplemental information only when they're available. Availability of information is varied and depends on many factors. Make sure to consider this when using SeenBy\(\) in your queries or in creating custom detections. For best results, we recommend using the SeenBy\(\) function with the DeviceInfo table.

### Example: Obtain list of onboarded devices that have seen a device

```kusto
DeviceInfo 
| where OnboardingStatus <> "Onboarded" 
| limit 100 | invoke SeenBy()
```

## Related articles

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Get more query examples](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
