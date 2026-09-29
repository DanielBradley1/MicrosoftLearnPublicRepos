<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/indicator-manage -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Manage indicators in Microsoft Defender for Endpoint

1. In the navigation pane, select **Settings** > **Endpoints** > **Indicators** \(under **Rules**\).
2. Select the tab for the indicator type you want to manage, such as **File hashes**, **IP addresses**, **URLs/domains**, or **Certificates**.
3. Update the indicator details, and then select **Save**. To remove the indicator from the list, select **Delete**.

## Import a list of IoCs

You can upload indicators from a CSV file that defines indicator attributes, actions, and other details.

Download the sample indicators CSV file from the **Indicators** import page \(under **Settings** > **Endpoints** > **Indicators**\) to review the supported column attributes.

1. In the navigation pane, select **Settings** > **Endpoints** > **Indicators** \(under **Rules**\).
2. Select the tab of the entity type you'd like to import indicators for.
3. Select **Import** > **Choose file**.
4. Select **Import**. Repeat for all the files you'd like to import.
5. Select **Done**.

Note

Only 500 indicators can be uploaded for each batch. Attempting to import indicators with specific categories requires the string to be written in Pascal case convention and only accepts the category list available in the Microsoft Defender portal.

The following table shows the supported parameters.

| Parameter | Type | Description |
| --- | --- | --- |
| indicatorType | Enum | Type of the indicator. Possible values are: `FileSha1`, `FileSha256`, `IpAddress`, `DomainName`, and `Url`.  <br>**Required** |
| indicatorValue | String | Identity of the [Indicator API resource](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) entity.  <br>**Required** |
| action | Enum | The action that is taken if the indicator is discovered in the organization. Possible values are: `Allowed`, `Audit`, `BlockAndRemediate`, `Warn`, and `Block`.  <br>**Required** |
| title | String | Indicator alert title.  <br>**Required** |
| description | String | Description of the indicator.  <br>**Required** |
| expirationTime | DateTimeOffset | The expiration time of the indicator in the following format `YYYY-MM-DDTHH:MM:SS.0Z`. The indicator gets deleted if the expiration time passes and whatever happens at the expiration time occurs at the seconds \(SS\) value.  <br>**Optional** |
| severity | Enum | The severity of the indicator. Possible values are: `Informational`, `Low`, `Medium`, and `High`.  <br>**Optional** |
| recommendedActions | String | TI indicator alert recommended actions.  <br>**Optional** |
| rbacGroups | String | Comma-separated list of RBAC groups the indicator would be applied to.  <br>**Optional** |
| category | String | Category of the alert. Examples include: Execution and credential access.  <br>**Optional** |
| mitretechniques | String | MITRE techniques code/id \(comma separated\). For more information, see [Enterprise tactics](https://attack.mitre.org/tactics/enterprise/).  <br>**Optional**  <br>It's recommended to provide a value in the category field when you specify a MITRE technique in the mitretechniques field. |
| GenerateAlert | String | Whether the alert should be generated. Possible Values are: `True` or `False`.  <br>**Optional** |

Note

Classless Inter-Domain Routing \(CIDR\) notation for IP addresses is not supported. For more information, see [Microsoft Defender for Endpoint alert categories are now aligned with MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

Network indicators do not support the action type, `BlockAndRemediate`. If a network indicator is set to `BlockAndRemediate`, it won't import.

Watch this video to learn how Microsoft Defender for Endpoint provides multiple ways to add and manage Indicators of compromise \(IoCs\).

<iframe src="https://learn-video.azurefd.net/vod/player?id=a4469df9-4f31-4ed0-9577-8b26ac5293ad" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## See also

- [Create indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview)
- [Create indicators for files](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file)
- [Create indicators for IPs and URLs/domains](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain)
- [Create indicators based on certificates](https://learn.microsoft.com/en-us/defender-endpoint/indicator-certificates)
- [Exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
