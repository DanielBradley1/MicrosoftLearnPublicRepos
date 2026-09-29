<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/exclusions -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Configure Defender for Identity detection exclusions in Microsoft Defender

This article explains how to configure [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity) detection exclusions in [Microsoft Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/overview-security-center).

Microsoft Defender for Identity enables the exclusion of specific IP addresses, computers, domains, or users from a number of detections.

For example, a **DNS Reconnaissance** alert could be triggered by a security scanner that uses DNS as a scanning mechanism. Creating an exclusion helps Microsoft Defender for Identity ignore such scanners and reduce false positives.

Note

- We recommend that you [tune an alert in Microsoft Defender XDR](https://learn.microsoft.com/en-us/microsoft-365/security/defender/investigate-alerts#tune-an-alert) instead of using exclusions. Alert tuning rules allow more granular conditions than exclusions, and allow you to review the alerts, which were tuned.
- Among the most common domains with [Suspicious communication over DNS](https://learn.microsoft.com/en-us/defender-for-identity/other-alerts#suspicious-communication-over-dns-external-id-2031) alerts, we observed the domains that were most frequently excluded from the alert. These domains are added to the exclusions list by default, but you have the option to remove them.

Important

As Defender for Identity detections move to the Microsoft Defender XDR detection engine, existing detection exclusions don't automatically carry over. After a detection moves, previously configured exclusions stop applying, and alerts that were previously suppressed can reappear. To preserve your tuning, re-create equivalent tuning by using [alert tuning rules](https://learn.microsoft.com/en-us/microsoft-365/security/defender/investigate-alerts#tune-an-alert) in the Microsoft Defender portal.

## How to add detection exclusions

To add detection exclusions, complete the following steps.

Note

When you replace an exclusion with an alert tuning rule, find the detection for the excluded entity. Then map it to the matching detector in alert tuning. After you create the rule, check that the detector shows under **Alert tuning** in the Microsoft Defender portal. This confirms that the alert scope is correct.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/)
2. Go to **System** > **Settings** and then **Identities**.

   ![Screenshot that shows the identities settings page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/settings-identities.png)
3. Select **Excluded entities**. You can set exclusions using two methods: **Exclusions by detection rule** and **Global excluded entities**.

   ![Screenshot of the excluded entities list.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/excluded-entities.png)

## Exclusions by detection rule

To configure exclusions for a specific detection rule, follow these steps:

1. Select **Exclusions by detection rule**.

   ![Screenshot of the exclusions by detection rule option.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/exclusions-by-detection-rule.png)
2. For each detection you want to configure, do the following steps:

   1. Select a detection rule from the list.
   2. View the detection rule details.

      ![Screenshot of the detection rule details.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/detection-rule-details.png)
   3. To add an exclusion, select the **Excluded entities** button.
   4. Choose the exclusion type, such as users, devices, domains, or IP addresses. Each rule supports different entity types. In this example, the choices are **Exclude devices** and **Exclude IP addresses**.

      ![Screenshot showing the options to exclude devices or IP addresses.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/exclude-devices-or-ip-addresses.png)
   5. After choosing the exclusion type, select the **+** button to add the exclusion.

      ![Screenshot of the add exclusion button.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/add-exclusion.png)
   6. Select **+ Add** to add the excluded entity to the list.

      ![Screenshot showing how to add an entity to be excluded.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/add-excluded-entity.png)
   7. Select **Exclude IP addresses** \(in this example\) to complete the exclusion.

      ![Screenshot showing the exclusion of IP addresses.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/exclude-ip-addresses.png)
   8. After you add exclusions, you can export or remove them. Return to the **Excluded entities** button. In this example, select **Exclude devices**. To export the list, select the down arrow button.

      ![Screenshot showing how to return to exclude devices.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/return-to-exclude-devices.png)
   9. To delete an exclusion, select the exclusion and select the trash icon. Deleting an exclusion removes it immediately and may cause related alerts to resume.

      ![Screenshot showing how to delete an exclusion.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/delete-exclusion.png)

## Global excluded entities

You can also configure exclusions by using **Global excluded entities**. Global exclusions let you exclude certain entities \(IP addresses, subnets, devices, or domains\) from all Defender for Identity detections. For example, if you exclude a device, the exclusion applies only to detections that use device identification.

1. Select **Global excluded entities** to see the categories of entities that you can exclude.

   ![Screenshot showing the global excluded entities.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/global-excluded-entities.png)
2. Choose an exclusion type. In this example, we selected **Exclude domains**.

   ![Screenshot showing the option to exclude domains.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/exclude-domains.png)
3. A pane opens where you can add a domain to be excluded. Add the domain you want to exclude.

   ![Screenshot showing how to add a domain to be excluded.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/add-excluded-domain.png)
4. The domain is added to the list. Select **Exclude domains** to complete the exclusion.

   ![Screenshot showing how to exclude domains.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/select-exclude-domains.png)
5. You'll then see the domain in the list of entities to be excluded from all detection rules. You can export the list, or remove the entities by choosing them and selecting the **Remove** button.

   ![Screenshot showing the list of global excluded entries.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/global-excluded-entries-list.png)

## Next steps

- [Configure event collection](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-event-collection)
- [Microsoft Defender for Identity community forum](https://aka.ms/MDIcommunity)
