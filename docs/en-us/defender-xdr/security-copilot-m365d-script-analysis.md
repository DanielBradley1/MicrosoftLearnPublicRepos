<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-script-analysis -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Script analysis with Microsoft Copilot in Microsoft Defender

Through AI-powered investigation capabilities from [Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/microsoft-security-copilot) in the Microsoft Defender portal, security teams can speed up their analysis of malicious or suspicious scripts and command lines.

This guide describes what the script analysis capability is and how it works, including how you can provide feedback on the results generated.

## Before you begin

If you're new to Security Copilot, you should familiarize yourself with it by reading the following articles:

- [What is Security Copilot?](https://learn.microsoft.com/en-us/security-copilot/microsoft-security-copilot)
- [Security Copilot experiences](https://learn.microsoft.com/en-us/security-copilot/experiences-security-copilot)
- [Get started with Security Copilot](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot)
- [Understand authentication in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/authentication)
- [Prompting in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/prompting-security-copilot)

Most complex and sophisticated attacks like [Microsoft ransomware guidance](https://learn.microsoft.com/en-us/security/ransomware) evade detection through numerous ways, including the use of scripts and PowerShell command lines. Moreover, these scripts are often obfuscated, which adds to the complexity of detection and analysis. Security operations teams need to quickly analyze scripts to understand capabilities and apply appropriate mitigation, immediately stopping attacks from progressing further within a network.

The script analysis capability provides security teams added capacity to inspect scripts without using external tools. The script analysis capability also reduces the complexity of analysis, minimizing challenges and allowing security teams to quickly assess and identify a script as malicious or benign.

## Security Copilot integration in Microsoft Defender

The script analysis capability is available in the Microsoft Defender portal for customers who have provisioned access to Security Copilot.

Script analysis is also available in the Security Copilot standalone experience through the Microsoft Defender XDR plugin. For information about the Microsoft Defender XDR plugin, see [Preinstalled plugins in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/manage-plugins#preinstalled-plugins).

## Key script analysis features

You can access the script analysis capability within the attack story below the incident graph on an incident page and in the device timeline view. For more information, see [Investigate the device timeline](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines#investigate-device-timeline).

To begin analysis, perform the following steps:

1. Open an incident page then select an item on the left pane to open the attack story below the incident graph. Within the attack story, select an event with a script or command line that you want to analyze. Click **Analyze** to start the analysis.

   [![Screenshot that shows the script analysis button in the attack story view.](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/script-analyzer/copilot-defender-script-analysis-incident-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/script-analyzer/copilot-defender-script-analysis-incident.png#lightbox)

   Alternately, you can select an event to inspect in the device timeline view. On the file details pane, select **Analyze** to run the script analysis capability.

   [![Screenshot that shows the Analyze button in the device timeline.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/copilot-defender-script-device-timeline-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/copilot-defender-script-device-timeline.png#lightbox)
2. Copilot runs script analysis and displays the results in the Copilot pane. Select **Show code** to expand the script, or **Hide code** to close the expansion.

   [![Screenshot highlighting the show or hide code option within the script analysis results.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/show-code-script-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/show-code-script.png#lightbox)
3. Select **Show MITRE techniques** to view the MITRE ATT&CK techniques associated with the script. This information helps you understand the techniques used by the script and how it can impact your environment. Select **Hide MITRE techniques** to close the expansion.

   [![Screenshot highlighting the show or hide MITRE techniques option within the script analysis results.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/hide-mitre-script-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/hide-mitre-script.png#lightbox)
4. Select the **More actions** ellipsis \(...\) on the upper right of the script analysis card to copy or regenerate the results, or view the results in the Security Copilot standalone experience. Selecting **Open in Security Copilot** opens a new tab to the Copilot standalone portal where you can input prompts and access other plugins.

   ![Screenshot that shows the More actions option in the Copilot script analysis card.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-script-analysis/script-analysis-options.png)

5. Review the results and use the information to guide your investigation and response to the incident.

## Sample script analysis prompt

In the Security Copilot standalone portal, you can use the following prompt identify and analyze scripts:

- *Identify the scripts in Defender incident {incident ID}. Are these malicious scripts?*

Tip

When analyzing scripts in the Security Copilot portal, Microsoft recommends including the word ***Defender*** in your prompts to ensure that the script analysis capability delivers the results.

## Provide feedback on script analysis

Microsoft highly encourages you to provide feedback to Copilot, as it's crucial for a capability's continuous improvement. You can provide feedback on the results by selecting the feedback icon ![Screenshot of the feedback control used to submit feedback for Copilot responses in Defender cards.](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/copilot-defender-feedback.png) found at the end of the script analysis card.

## Related content

- [Learn about other Security Copilot embedded experiences](https://learn.microsoft.com/en-us/security-copilot/experiences-security-copilot)
- [Privacy and data security in Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
