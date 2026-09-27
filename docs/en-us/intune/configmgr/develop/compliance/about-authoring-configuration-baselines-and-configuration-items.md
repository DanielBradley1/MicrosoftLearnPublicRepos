<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About authoring configuration baselines and configuration items

Configuration Manager supports the authoring of configuration data, which consists of configuration baselines and configuration items. Configuration Manager presents this configuration data in a user-friendly format called DCM Digest. This format is a specialized XML document that Configuration Manager uses. You can author configuration data by using the Configuration Manager console, or by directly authoring a DCM Digest XML file.

When you create configuration data with the Configuration Manager console, you can export it into a .cab file. When configuration data is imported into Configuration Manager, the format is DCM Digest XML only.

## Authoring configuration data

Create configuration data in the following ways:

- You can create configuration data externally with an XML editor. If you then package it as a .cab file, you can import it into Configuration Manager.
- You can create configuration data within Configuration Manager by using the following wizards:

  - Create Application Configuration Item Wizard
  - Create Operating System Configuration Item Wizard
  - Create Configuration Baseline

Important

You create and manage software update configuration items through the software updates management feature in Configuration Manager. You can reference these configuration items by configuration baselines. However, don't directly author them by using configuration items or the DCM Digest.

You can also import configuration data that software vendors and solution providers have published.

Note

You can digitally sign published configuration data. Then you can verify the publishing source and be sure that no one has tampered with the data. If the digital signature verification check fails, Configuration Manager warns you to continue with the import. Only import configuration data from external sources if it has a valid digital signature from a trusted publisher.

After the site imports the configuration data, you can then work with it in the Configuration Manager console.

## Next steps

[About authoring configuration baselines and items](https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-authoring-configuration-baselines-and-configuration-items)
