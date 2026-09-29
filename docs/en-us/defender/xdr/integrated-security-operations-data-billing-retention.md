<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Data ingestion and billing for ISOC in Microsoft Defender \(preview\)

Integrated Security Operations Center \(ISOC\) in Microsoft Defender supports Microsoft security data and additional Microsoft and non-Microsoft security data.

Note

ISOC is in preview. Capabilities and availability might change during the preview period.

## How data is handled

Native Microsoft Defender data is available directly in the Microsoft Defender experience and doesn't need to be separately ingested into an ISOC workspace.

Other supported Microsoft and non-Microsoft data can be connected through an ISOC workspace by using data connectors.

## Microsoft security data

ISOC supports Microsoft security data from the following sources:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Cloud
- Microsoft Entra Identity Protection logs
- Azure Activity and audit logs through a connector
- Office 365 Activity and audit logs through a connector

Eligible customers with Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7 can use supported Microsoft Defender security data as part of the ISOC experience.

Note

During this phase of the preview, eligible customers receive 30 days of included retention for Defender data.

For Microsoft 365 E5 plan details and pricing, see [Microsoft 365 E5 for Enterprise](https://www.microsoft.com/microsoft-365/enterprise/e5#Pricing).

To compare the security capabilities included with Microsoft 365 enterprise plans, see [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

## Additional Microsoft and non-Microsoft security data

An ISOC workspace is required to ingest additional Microsoft and non-Microsoft security data through more than 500 data connectors.

Additional ingestion charges might apply depending on the data you ingest.

## Next steps

- [Learn more about ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview)
- [Create an ISOC workspace in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace)
