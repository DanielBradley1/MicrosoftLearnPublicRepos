<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/dcs-inspection -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Integrate Microsoft Data Classification Services with Microsoft Defender for Cloud Apps

Important

File policies retire on January 6, 2027. To maintain file-based data protection, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

Microsoft Defender for Cloud Apps enables you to natively use the Microsoft Data Classification Service to classify the files in your cloud apps. Microsoft Data Classification Service provides a unified information protection experience across Microsoft 365, Microsoft Information Protection, and Microsoft Defender for Cloud Apps. The classification service allows you to extend your data classification efforts to the third-party cloud apps protected by Microsoft Defender for Cloud Apps, using the decisions you already made across an even greater number of apps.

Note

The Microsoft Data Classification Service integration is currently available in the US, Europe, Australia, India, Canada, Japan, and APAC.

Note

To enable the Data Classification Service option in File Policies, the "Microsoft 365" App Connector is required.

## Enable content inspection with Data Classification Services

You can set the **Inspection method** to use the **Microsoft Data Classification Service** with no additional configuration required. This option is useful when creating a data leak prevention policy for your files in Microsoft Defender for Cloud Apps.

1. In the [file policy](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies) page, under **Inspection method**, select **Data Classification Service**. You can also set the **Inspection method** in the [session policy](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad) page with **Control file download \(with inspection\)** selected.

   ![Data Classification Service inspection method setting in file policy.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/dcs-enable.png)

2. Select whether the policy should apply when **any** or **all** of the criteria are met.
3. **Choose inspection type** by selecting the **Sensitive information types**.

   ![Screenshot of the file policy configuration page with sensitive information types selected as the Data Classification Service inspection type.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/dcs-sensitive-information-type.png)

4. You can use the [default sensitive information types](https://learn.microsoft.com/en-us/microsoft-365/compliance/sensitive-information-type-entity-definitions) to define what happens to files protected by Microsoft Defender for Cloud Apps. You can also reuse any of your [Microsoft 365 custom sensitive information types](https://learn.microsoft.com/en-us/microsoft-365/compliance/create-a-custom-sensitive-information-type).

   Note

   You can configure your policy to use advanced classification types such as [Fingerprints](https://learn.microsoft.com/en-us/microsoft-365/compliance/document-fingerprinting?view=o365-worldwide&preserve-view=true), [Exact Data Match](https://learn.microsoft.com/en-us/microsoft-365/compliance/sit-learn-about-exact-data-match-based-sits), and [trainable classifiers](https://learn.microsoft.com/en-us/microsoft-365/compliance/classifier-get-started-with).
5. Optionally, you can unmask the last four characters of a match. By default, matches are masked and shown in their context, and include the 40 characters before and after the match. If you select this checkbox, the policy unmasks the last four characters of the match itself.
6. Leveraging file policies, you can also set alerts and governance actions for the policy. For more information, see [file policies](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies) and [governance actions](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions). Leveraging session policies, you can also monitor and control actions in real-time when a file matches a DCS type. For more information, see [session policy](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad).

Setting these policies enables you to easily extend the strength of the Microsoft 365 DLP capabilities to all your other sanctioned cloud apps and protect the data stored in them with the full toolset provided to you by Microsoft Defender for Cloud Apps – such as the ability to [automatically apply Microsoft Information Protection sensitivity labels](https://learn.microsoft.com/en-us/defender-cloud-apps/azip-integration) and the ability to control sharing permissions.

## Examine evidence \(preview\)

Defender for Cloud Apps already includes the ability to explore policy file matches that contain sensitive information types \(SITs\). Now Defender for Cloud Apps also allows you to differentiate between multiple SITs in the same file match. This feature, known as short evidence, lets Defender for Cloud Apps better manage and protect your organization's sensitive data.

The short evidence feature is relevant for file policies that contain content inspection using the Data Classification Service \(DCS\) engine.

1. Configure a file policy and choose the relevant DCS classifiers. If you already use a file policy with DCS, the short evidence feature will work for all files evaluated by that policy.
2. On the **Policies** page, enter the relevant file policy and select the policy matches.
3. You can then analyze the different SITs with a clickable, color-coding distinguisher.

[![Configure short evidence.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/short-evidence.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/short-evidence.png#lightbox)

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
