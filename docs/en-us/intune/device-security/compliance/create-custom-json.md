<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/compliance/create-custom-json -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Custom compliance JSON files for Microsoft Intune

To support [custom settings for compliance](https://learn.microsoft.com/en-us/intune/device-security/compliance/custom-settings) for Microsoft Intune, create a JSON file that identifies the settings and value pairs you want to use for custom compliance. The JSON defines what a discovery script evaluates for compliance on the device.

Include the JSON file in a compliance policy when you configure a policy to assess custom compliance settings.

## Requirements

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> - Linux:
> 
>   - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
>   - RedHat Enterprise Linux 9 or 10
>   - macOS
> 
> - Windows

A correctly formatted JSON file must include the following information:

- **SettingName** - The name of the custom setting to use for base compliance. This name is case-sensitive.
- **Operator** - Represents a specific action that's used to build a compliance rule. For options, see the list of supported operators in this article.
- **DataType** - The type of data that you can use to build your compliance rule. For options, see the following list of *supported DataTypes*.
- **Operand** - Represents the values that the operator works on.
- **MoreInfoURL** - A URL that device users can view and use to learn more about the compliance requirement if their device is noncompliant for a setting. You can also use this URL to link to instructions to help users bring their device into compliance for this setting.
- **RemediationStrings** - Information that shows in the Company Portal when a device is noncompliant to a setting. This information helps users understand the remediation options to bring a device to a compliant state. There must be at least one string for the language `en_US`. You can add other remediation string languages as needed, as demonstrated in the [example](#example-json-file) provided later in this article.

Your policy can be up to 100 KB and include 100 rules.

**Supported operators**:

- IsEquals
- NotEquals
- GreaterThan
- GreaterEquals
- LessThan
- LessEquals

**Supported DataTypes**:

- Boolean
- Int64
- Double
- String
- DateTime
- Version

**Supported Languages**:

- cs\_CZ
- da\_DK
- de\_DE
- el\_GR
- en\_US
- es\_ES
- fi\_FI
- fr\_FR
- hu\_HU
- it\_IT
- ja\_JP
- ko\_KR
- nb\_NO
- nl\_NL
- pl\_PL
- pt\_BR
- ro\_RO
- ru\_RU
- sv\_SE
- tr\_TR
- zh\_CN
- zh\_TW

For more information, see [Available languages for Windows](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/available-language-packs-for-windows).

## Example JSON file

```json
{
"Rules":[
    {
       "SettingName":"BiosVersion",
       "Operator":"GreaterEquals",
       "DataType":"Version",
       "Operand":"2.3",
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language":"en_US",
             "Title":"BIOS Version needs to be upgraded to at least 2.3. Value discovered was {ActualValue}.",
             "Description": "BIOS must be updated. Please refer to the link above"
          },
          {
             "Language":"de_DE",
             "Title":"BIOS-Version muss auf mindestens 2.3 aktualisiert werden. Der erkannte Wert lautet {ActualValue}.",
             "Description": "BIOS muss aktualisiert werden. Bitte beziehen Sie sich auf den obigen Link"
          }
       ]
    },
    {
       "SettingName":"TPMChipPresent",
       "Operator":"IsEquals",
       "DataType":"Boolean",
       "Operand":true,
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language": "en_US",
             "Title": "TPM chip must be enabled.",
             "Description": "TPM chip must be enabled. Please refer to the link above"
          },
          {
             "Language": "de_DE",
             "Title": "TPM-Chip muss aktiviert sein.",
             "Description": "TPM-Chip muss aktiviert sein. Bitte beziehen Sie sich auf den obigen Link"
          }
       ]
    },
    {
       "SettingName":"Manufacturer",
       "Operator":"IsEquals",
       "DataType":"String",
       "Operand":"Microsoft Corporation",
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language": "en_US",
             "Title": "Only Microsoft devices are supported.",
             "Description": "You are not currently using a Microsoft device."
          },
          {
             "Language": "de_DE",
             "Title": "Nur Microsoft-Geräte werden unterstützt.",
             "Description": "Sie verwenden derzeit kein Microsoft-Gerät."
          }
       ]
    }
 ]
}
```

## Next steps

- [Use custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/custom-settings)
- [Create a discovery script for custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-custom-script)
- [Create a compliance policy](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-policy)
