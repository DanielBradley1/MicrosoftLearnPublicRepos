<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-shared-device-settings-ipados -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# iPads with no user affinity

iPads used in earlier grades are commonly enrolled with no user affinity to simplify the user experience for younger students and to allow sharing of devices. For more information, please refer to [Enroll devices with Automated Device Enrollment](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-ios-ade).

These iPads generally have additional restrictions that are not suitable for 1:1 devices.

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS and macOS devices](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/)
- [Restrictions payload](https://developer.apple.com/documentation/devicemanagement/restrictions)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

- [**Settings**](#tabpanel_1_settings)
- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/graph.svg)](#tabpanel_1_graph)

| **Category** | **Property** | **Value** | **Notes** | **Payload property** |
| --- | --- | :---: | --- | --- |
| Restrictions | **Allow Account Modification** | False | Disables modification of accounts such as Apple IDs and Internet-based accounts such as Mail, Contacts, and Calendar. | [allowAccountModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Bookstore** | False | Removes the Book Store tab from the Books app. | [allowBookstore](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Enterprise Book Backup** | False | Disables backup of Enterprise books. | [allowEnterpriseBookBackup](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Enterprise Book Metadata Sync** | False | Disables sync of Enterprise books, notes, and highlights. | [allowEnterpriseBookMetadataSync](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Fingerprint For Unlock** | False | Prevents Touch ID or Face ID from unlocking a device. | [allowFingerprintForUnlock](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Fingerprint Modification** | False | Prevents the user from modifying Touch ID or Face ID. | [allowFingerprintModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Passcode Modification** | False | Prevents adding, changing, or removing the passcode. | [allowPasscodeModification](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Allow Password Auto Fill** | False |  | [allowPasswordAutoFill](https://developer.apple.com/documentation/devicemanagement/restrictions) |
| Restrictions | **Safari Allow Autofill** | False | Disables Safari AutoFill for passwords, contact info, and credit cards and also prevents using the Keychain for AutoFill. | [safariAllowAutoFill](https://developer.apple.com/documentation/devicemanagement/restrictions) |

Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - iPads - No user affinity**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - iPads - No user affinity","description":"","platforms":"iOS","technologies":"mdm,appleRemoteManagement","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationGroupSettingCollectionInstance","settingDefinitionId":"com.apple.applicationaccess_com.apple.applicationaccess","groupSettingCollectionValue":[{"children":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowaccountmodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowaccountmodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowbookstore","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowbookstore_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowenterprisebookbackup","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowenterprisebookbackup_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowenterprisebookmetadatasync","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowenterprisebookmetadatasync_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowfingerprintforunlock","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowfingerprintforunlock_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowfingerprintmodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowfingerprintmodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowpasscodemodification","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowpasscodemodification_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_allowpasswordautofill","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_allowpasswordautofill_false","children":[]}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"com.apple.applicationaccess_safariallowautofill","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"com.apple.applicationaccess_safariallowautofill_false","children":[]}}]}]}}]}
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
