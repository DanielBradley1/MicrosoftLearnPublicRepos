<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Attack surface reduction \(ASR\) rules deployment guide

Attack surface reduction \(ASR\) rules target risky software behavior on Windows devices that attackers commonly exploit through malware \(for example, launching scripts that download files, running obfuscated scripts, and injecting code into other processes\). For an introduction to ASR rules and their requirements, see [Attack surface reduction \(ASR\) rules overview](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview).

This guide helps you plan, test, implement, and manage your ASR rules deployment to effectively stop advanced threats like human-operated ransomware.

Important

This guide provides images and examples to help you decide how to configure ASR rules. These images and examples might not reflect the best configuration options for your environment.

[![Diagram of the ASR rules deployment phases: plan, test, enable, and maintain.](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-deployment-phases.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-deployment-phases.png#lightbox)

## Important predeployment caveat

Typically, you can enable the [standard protection rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#asr-rules) in **Block** or **Warn** mode without testing. You should test other ASR rules in **Audit** mode before you switch them to **Block** or **Warn** mode.

## Before you begin

Before you start the deployment process, review the following documentation:

- [Overview of attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-overview)
- [Attack surface reduction \(ASR\) rules reference](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference)

## Deployment steps

Use the following articles to plan, test, implement, and manage your ASR rules deployment:

1. [Plan ASR rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-plan): Determine infrastructure requirements, select business units and champions, and define team roles.
2. [Test ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test): Configure rules in **Audit** mode, review reports, and add exclusions.
3. [Enable ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-implement): Transition rules from **Audit** to **Block** mode, and expand to other deployment rings.
4. [Manage and monitor ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-operationalize): Monitor ongoing activity, manage false positives, and use advanced hunting.

## Related content

- [Attack surface reduction \(ASR\) rules overview](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)
- [Attack surface reduction \(ASR\) rules reference](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference)
- [Configure attack surface reduction \(ASR\) rules and exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure)
- [Attack surface reduction \(ASR\) rules report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report)
- [Attack surface reduction FAQ](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-faq)
- [Demystifying attack surface reduction rules - Part 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)
- [Demystifying attack surface reduction rules - Part 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)
- [Demystifying attack surface reduction rules - Part 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)
- [Demystifying attack surface reduction rules - Part 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)
