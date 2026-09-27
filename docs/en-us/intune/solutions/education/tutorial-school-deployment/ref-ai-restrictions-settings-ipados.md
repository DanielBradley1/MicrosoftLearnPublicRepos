<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-ai-restrictions-settings-ipados -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Apple Intelligence

This article summarizes restrictions for Apple Intelligence introduced in iPadOS 18.

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS and macOS devices](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/)
- [Restrictions payload](https://developer.apple.com/documentation/devicemanagement/restrictions)
- [iPadOS 18](https://www.apple.com/ipados/ipados-18)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

- [**Settings**](#tabpanel_1_settings)
- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/graph.svg)](#tabpanel_1_graph)

| **Category** | **Property** | **Value** | **Notes** | **Payload property** |
| --- | --- | :---: | --- | --- |
| Restrictions | **Allow Genmoji** | False | Prohibits creating new Genmoji. | [allowGenmoji](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Image Playground** | False | Prohibits the use of image generation. | [allowImagePlayground](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Image Wand** | False | Prohibits the use of Image Wand. | [allowImageWand](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Personalized Handwriting Results** | False |  | [allowPersonalizedHandwritingResults](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Writing Tool** | False | Disables Apple Intelligence writing tools. | [allowWritingTools](https://developer.apple.com/documentation/devicemanagement/restrictions) |

Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - iPads - Apple Intelligence**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - iPads - Apple Intelligence","description":"","platforms":"iOS","technologies":"mdm,appleRemoteManagement","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"com.apple.applicationaccess_com.apple.applicationaccess","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowgenmoji","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowgenmoji_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowimageplayground","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowimageplayground_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowimagewand","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowimagewand_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowpersonalizedhandwritingresults","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowpersonalizedhandwritingresults_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowwritingtools","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowwritingtools_false","children":[]}}]}]}}]}
```

1. Click *Try it* to open Graph Explorer.
2. Once Graph Explorer is open, select the ![](https://learn.microsoft.com/en-us/intune/media/icons/16/person.svg) user icon in the top right to sign-in and sign in with your Intune administrator organizational account.
3. Click **Run query** to create the policy in your tenant.

   Tip

   If it's the first time using Graph Explorer, you may need to authorize the application to access your tenant or to modify the existing permissions. This graph call requires *DeviceManagementConfiguration.ReadWrite.All* permissions. You can grant the required permissions by selecting **modify permissions** and then selecting **Consent**.
4. The policy is created in your tenant and can be edited to meet your requirements before assigning to groups.

Note

As of July 31 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.ReadWrite.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts
