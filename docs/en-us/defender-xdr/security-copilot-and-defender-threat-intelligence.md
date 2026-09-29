<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-copilot-and-defender-threat-intelligence -->
<!-- Sitemap-Last-Modified: 2026-08-02 -->

# Use Microsoft Security Copilot for threat intelligence

Microsoft Security Copilot is a cloud-based AI platform that provides a natural language copilot experience. It can help support security professionals in different scenarios, like incident response, threat hunting, and intelligence gathering. For more information about what it can do, read [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot).

Security Copilot customers receive access to Microsoft Threat Intelligence for each authenticated Copilot user. To ensure that you have access to Copilot, see the [Security Copilot purchase and licensing information](https://learn.microsoft.com/en-us/copilot/security/faq-security-copilot).

Once you have access to Security Copilot, the key features discussed in this article become accessible in either the Security Copilot portal or the [Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence#use-microsoft-copilot-in-defender-for-threat-intelligence).

## Know before you begin

If you're new to Security Copilot, you should familiarize yourself with it by reading these articles:

- [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)
- [Microsoft Security Copilot experiences](https://learn.microsoft.com/en-us/copilot/security/experiences-security-copilot)
- [Get started with Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot)
- [Understand authentication in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/authentication)
- [Prompting in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/prompting-security-copilot)

## Security Copilot integration with Microsoft Threat Intelligence

Security Copilot delivers information about threat actors, indicators of compromise \(IOCs\), tools, and vulnerabilities, as well as contextual threat intelligence from Microsoft Threat Intelligence. You can use the prompts and promptbooks to investigate incidents, enrich your hunting flows with threat intelligence information, or gain more knowledge about your organization's or the global threat landscape.

- Be clear and specific with your prompts. You might get better results if you include specific threat actor names or IOCs in your prompts. It might also help if you add **threat intelligence** to your prompt, like:

  - Show me threat intelligence data for Aqua Blizzard.
  - Summarize threat intelligence data for "malicious.com."

- Be specific when referencing an incident \(for example, "incident ID 15324"\).
- Experiment with different prompts and variations to see what works best for your use case. Chat AI models vary, so iterate and refine your prompts based on the results you receive.
- Copilot saves your prompt sessions. To see the previous sessions, from the Security Copilot [Home menu](https://learn.microsoft.com/en-us/copilot/security/navigating-security-copilot#home-menu), go to **My sessions**.

  ![Screenshot that shows the Microsoft Security Copilot Home menu with My sessions highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-and-defender-threat-intelligence/copilot-my-sessions.png)


  Note


  For a walkthrough on Copilot, including the pin and share feature, read [Navigate Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/navigating-security-copilot).

[Learn more about creating effective prompts](https://learn.microsoft.com/en-us/copilot/security/prompting-tips)

## Key features

Security Copilot lets security teams understand, prioritize, and take action on threat intelligence information immediately.

You can ask about a threat actor, attack campaign, or any other threat intelligence that you want to know more about, and Copilot generates responses based on threat analytics reports, intel profiles and articles, and other Microsoft Threat Intelligence content.

You can also select any of the built-in prompts that are available in the Defender portal to do the following actions:

- **Summarize** the latest threats related to your organization.
- **Prioritize** which threats to focus on based on your environment's highest exposure level.
- **Ask** about the threat actors targeting a specific industry.

[Learn more about using Copilot in Defender for threat intelligence](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence#use-microsoft-copilot-in-defender-for-threat-intelligence)

## Turn on the Security Copilot integration

1. Go to [Microsoft Security Copilot](https://go.microsoft.com/fwlink/?linkid=2247989) and sign in with your credentials.
2. Make sure that the Microsoft Threat Intelligence plugin is turned on. In the prompt bar, select the **Sources** icon.

   ![Screenshot of the prompt bar in Microsoft Security Copilot with the Sources icon highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-and-defender-threat-intelligence/copilot-prompts-bar-sources.png)


   In the **Manage sources** pop-up window that appears, under **Plugins**, confirm that the **Microsoft Threat Intelligence** toggle is turned on, then close the window.


   ![Screenshot of the Manage plugins pop-up window with the Microsoft Threat Intelligence plugin highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-and-defender-threat-intelligence/copilot-manage-plugins.png)


   Note


   Some roles can turn the toggle on or off for plugins like Microsoft Threat Intelligence. For more information, read [Manage plugins in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/manage-plugins).

3. Enter your prompt in the prompt bar.

### Built-in system features

Security Copilot has built-in system features that can get data from the different plugins that are turned on.

To view the list of built-in system capabilities for Microsoft Threat Intelligence:

1. In the prompt bar, select the **Prompts** icon.

   ![Screenshot of the prompt bar in Microsoft Security Copilot with the Prompts icon highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-and-defender-threat-intelligence/copilot-prompts-bar-prompts.png)

2. Select **See all system capabilities**. The *Microsoft Threat Intelligence* section lists all the available capabilities that you can use.

Copilot also has the following promptbooks that also deliver information from Microsoft Threat Intelligence:

- [**Check impact of an external threat article**](https://learn.microsoft.com/en-us/copilot/security/using-promptbooks#check-impact-of-an-external-threat-article) – Analyzes an external or third-party article to extract related IOCs, summarize the intelligence, and generate hunting queries so you can assess the potential impact of the threat reported in the article to your organization.
- [**Threat actor profile**](https://learn.microsoft.com/en-us/copilot/security/using-promptbooks#threat-actor-profile) – Generates a report profiling a known threat actor, including suggestions to defend against their common tools and tactics.
- [**Threat Intelligence 360 report based on MDTI article**](https://learn.microsoft.com/en-us/copilot/security/using-promptbooks#threat-intelligence-360-report-based-on-mdti-article) – Analyzes a Microsoft Threat Intelligence article to extract related IOCs, summarize the intelligence, and generate hunting queries so you can assess the potential impact of the threat reported in the article to your organization.
- [**Vulnerability impact assessment**](https://learn.microsoft.com/en-us/copilot/security/using-promptbooks#vulnerability-impact-assessment) – Generates a report summarizing the intelligence for a known vulnerability, including steps on how to address it.

To view these promptbooks, in the prompt bar, select the **Prompts** icon then select **See all promptbooks**.

## Sample Microsoft Threat Intelligence prompts

You can use many prompts to get information from Microsoft Threat Intelligence. This section lists some ideas and examples.

### General information about threat intelligence trends

Get threat intelligence from threat articles and threat actors.

**Sample prompts** :

- Summarize the recent threat intelligence.
- Show me the latest threat articles.
- Get threat articles related to ransomware in the last six months.

### Threat actor mapping and infrastructure

Get information on threat actors and the tactics, techniques, and procedures \(TTPs\), sponsored states, industries, and IOCs associated with them.

**Sample prompts**:

- Tell me more about Silk Typhoon.
- Share the IOCs associated with Silk Typhoon.
- Share the TTPs associated with Silk Typhoon.
- Share threat actors associated with Russia.

### Vulnerability data by CVE

Get contextual information and threat intelligence on Common Vulnerabilities and Exposures \(CVEs\), which are derived from Microsoft Threat Intelligence articles, [threat analytics reports](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics), and data from [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) and [Microsoft Defender External Attack Surface Management](https://learn.microsoft.com/en-us/azure/external-attack-surface-management/overview).

**Sample prompts**:

- Share the technologies that are susceptible to the vulnerability CVE-2021-44228.
- Summarize the vulnerability CVE-2021-44228.
- Show me the latest CVEs.
- Show me threat actors associated with CVE-2021-44228.
- Show me the threat articles associated with CVE-2021-44228.

### Indicator data in relation to threat intelligence

Get detailed information about an indicator \(for example, IP addresses, domains, and file hashes\) based on the numerous [data sets](https://learn.microsoft.com/en-us/defender-xdr/entity-page-threat-intelligence) available in Microsoft Threat Intelligence, including reputation scores, WHOIS information, domain name system \(DNS\), host pairs, and certificates.

**Sample prompts**:

- What can you tell me about the domain *<domain name>*?
- Show me indicators related to *<domain name>*.
- Show me all resolutions for *<domain name>*.
- Show me host pairs related to *<domain name>*.
- Show me the reputation of the host *<host name>*.
- Show me all resolutions for IP address *<IP address>*.
- Show me the open services in *<IP address>*.

### Malware information

Get detailed information about a specific malware detection, which is derived from the [Microsoft Security Intelligence threat encyclopedia](https://www.microsoft.com/en-us/wdsi/threats/threat-search).

**Sample prompt**:

- What can you tell me about Ransom:Win32/WannaCrypt?

## Provide feedback

Your feedback on the Microsoft Threat Intelligence integration in Security Copilot helps with development. To provide feedback, in Copilot, select **How's this response?** at the bottom of each completed prompt and choose any of the following options:

- **Looks right** - Select this button if the results are accurate, based on your assessment.
- **Needs improvement** - Select this button if any detail in the results is incorrect or incomplete, based on your assessment.
- **Inappropriate** - Select this button if the results contain questionable, ambiguous, or potentially harmful information.

For each feedback button, you can provide more information in the next dialog box that appears. Whenever possible, and when the result is **Needs improvement**, write a few words explaining what can be done to improve the outcome. If you entered prompts specific to threat intelligence and the results aren't related, then include that information.

## Privacy and data security in Security Copilot

When you interact with Security Copilot to get Microsoft Threat Intelligence data, Copilot pulls that data from Microsoft Threat Intelligence. The prompts, the data retrieved, and the output shown in the prompt results are processed and stored within the Copilot service. [Learn more about privacy and data security in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security)

## Related content

- [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)
- [Privacy and data security in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security)
- [Microsoft Threat Intelligence in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence)
