<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-pua -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Detect and block potentially unwanted applications with Microsoft Defender for Endpoint on macOS

The potentially unwanted application \(PUA\) protection feature in Microsoft Defender for Endpoint on macOS can detect and block PUA files on endpoints in your network.

These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have poor reputation.

These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.

## How it works

Microsoft Defender for Endpoint on macOS can detect and report PUA files. When configured in blocking mode, PUA files are moved to the quarantine.

When a PUA is detected on an endpoint, Microsoft Defender for Endpoint on macOS presents a notification to the user, unless notifications are disabled. The threat name contains the word "Application".

## Configure PUA protection

PUA protection in Microsoft Defender for Endpoint on macOS can be configured in one of the following ways:

- **Off**: PUA protection is disabled.
- **Audit**: PUA files are reported in the product logs, but not in Microsoft Defender portal. No notification is presented to the user and no action is taken by the product.
- **Block**: PUA files are reported in the product logs and in Microsoft Defender portal. The user is presented with a notification and action is taken by the product.

Warning

By default, PUA protection is configured in **Audit** mode.

You can configure how PUA files are handled from the command line or from the management console.

### Use the command-line tool to configure PUA protection

In Terminal, execute the following command to configure PUA protection:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### Use the management console to configure PUA protection:

In your enterprise, you can configure PUA protection from a management console, such as JAMF or Intune, similarly to how other product settings are configured. For more information, see the [Threat type settings](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences#threat-type-settings) section of the [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences) article.

### Test PUA protection

You're able to test PUA protection by going to [Potentially unwanted applications \(PUA\) demonstration](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-demonstration-potentially-unwanted-applications).

## Related articles

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
