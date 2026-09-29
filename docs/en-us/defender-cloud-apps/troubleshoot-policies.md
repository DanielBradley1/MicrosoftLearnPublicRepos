<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshoot-policies -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Troubleshooting Microsoft Defender for Cloud Apps policies

This article describes the process for troubleshooting policy creation in Defender for Cloud Apps.

## Troubleshooting

The following chart has the description and resolution for errors you might see for policies.

| Error | Description | Resolution |
| --- | --- | --- |
| **The policy <*name*> was automatically disabled due to a configuration error** | If you get this error in Microsoft Defender for Cloud Apps, it means that you need to fix the configuration of the indicated policy. When you create a Microsoft Defender for Cloud Apps policy, you often make use of other objects created within Defender for Cloud Apps or the Security and Compliance Center such as IP tags or custom sensitive types. If the IP tag or custom sensitive type you used in the policy is deleted, the policy will automatically be disabled, and you'll receive this error. This message might also indicate a more general configuration error such as a filter that is too complex. | To restore the policy, edit the policy and fix every configuration error mentioned. This error usually means you need to remove any deleted objects from the policy filters and save the policy. |

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
