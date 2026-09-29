<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/software -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Software resource type

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | Software ID |
| Name | String | Software name |
| Vendor | String | Software publisher name |
| Weaknesses | Long | Number of discovered vulnerabilities |
| publicExploit | Boolean | Public exploit exists for some of the vulnerabilities |
| activeAlert | Boolean | Active alert is associated with this software |
| exposedMachines | Long | Number of exposed devices |
| impactScore | Double | Exposure score impact of this software |
