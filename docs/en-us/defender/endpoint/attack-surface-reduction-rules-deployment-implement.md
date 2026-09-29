<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-implement -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Enable your attack surface reduction \(ASR\) rules deployment

This article is part of the [Attack surface reduction \(ASR\) rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment).

After testing ASR rules in Audit mode, transition them to **Block** or **Warn** mode, starting with your first deployment ring. This article covers how to move ASR rules from Audit to Block or Warn mode in your first deployment ring, and then safely broaden your deployment across additional rings.

> [![Diagram of the steps to implement ASR rules: transition from Audit to Block mode, then expand to additional rings.](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-implementation-steps.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-implementation-steps.png#lightbox)

## Step 1: Transition ASR from Audit to Block

Perform the following steps to transition ASR rules from Audit mode to Block or Warn mode for your first deployment ring.

1. After you determine all required exclusions for rules in **Audit** mode, start setting some rules to **Block** or **Warn** mode. Start with the rule with the fewest triggered events. For instructions, see [Configure attack surface reduction \(ASR\) rules and exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure).
2. Review [ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor). Also review feedback from your champions.
3. Refine exclusions or create new exclusions as necessary.

Tip

Rule exclusions are better than turning off rules or switching them back to **Audit** mode.

Take advantage of the **Warn** mode in available rules to limit disruptions. **Warn** mode enables you to capture triggered events and view potential disruptions without actually blocking user access \(they can click through the warning notification\). For more information, see [ASR rule modes](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#modes-for-asr-rules).

## Step 2: Expand deployment to ring n + 1

When you're confident you correctly configured ASR rules for ring 1, you can widen the scope of your deployment to the next ring \(ring n + 1\).

The deployment process for each subsequent ring is:

1. Enable ASR rules in **Audit** mode.
2. Review [ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor).
3. [Create exclusions as necessary](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules).
4. Review ASR rule activity and refine exclusions.
5. Set rules to **Block** mode.
6. Review [ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor).
7. [Create exclusions as necessary](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules).
8. Disable problematic rules or switch them back to **Audit** mode.

## Related content

- [Attack surface reduction \(ASR\) rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment)
- [Plan your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-plan)
- [Test your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test)
- [Manage and monitor your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-operationalize)
- [Attack surface reduction \(ASR\) rules overview](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)
- [Configure attack surface reduction \(ASR\) rules and exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure)
