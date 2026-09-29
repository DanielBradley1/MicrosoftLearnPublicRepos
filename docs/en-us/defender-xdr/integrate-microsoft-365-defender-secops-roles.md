<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/integrate-microsoft-365-defender-secops-roles -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Step 4. Define Microsoft Defender XDR roles, responsibilities, and oversight

**Applies to:**

- Microsoft Defender XDR

This article maps Security Operations Center \(SOC\) team roles and responsibilities to Microsoft Defender XDR tasks so you can integrate the service into your existing security operations structure.

Your organization must establish ownership and accountability of the Microsoft Defender XDR licenses, configurations, and administration as initial tasks before any operational roles can be defined. Typically, the ownership of the licenses, subscription costs, and administration of Microsoft 365 and Enterprise Security + Mobility \(EMS\) services \(which may include Microsoft Defender XDR\) fall outside the SOC teams. SOC teams should work with those individuals to ensure proper oversight of Microsoft Defender XDR.

Many modern SOCs assign its team members to categories based on their skillsets and functions. For example:

- A threat intelligence team assigned to tasks related to lifecycle management of threat and analytics functions.
- A monitoring team comprised of SOC analysts responsible for maintaining logs, alerts, events, and monitoring functions.
- An engineering & operations team assigned to engineer and optimize security devices.

SOC team roles and responsibilities for Microsoft Defender XDR would naturally integrate into the threat intelligence, monitoring, and engineering & operations teams.

The following table breaks out each SOC team's roles and responsibilities and how their roles integrate with Microsoft Defender XDR.

| SOC team | Roles and responsibilities | Microsoft Defender XDR tasks |
| :--- | :--- | :--- |
| SOC Oversight | - Performs SOC governance<br>- Establishes daily, weekly, monthly processes<br>- Provides training and awareness<br>- Hires staff, participates in peer groups and meetings<br>- Conducts Blue, Red, Purple team exercises | - Microsoft Defender portal access controls<br>- Maintains feature/URL and licensing update register<br>- Maintains communication with IT, legal, compliance, and privacy stakeholders<br>- Participates in change control meetings for new Microsoft 365 or Microsoft Azure initiatives |
| Threat Intelligence & Analytics | - Threat intel feed management<br>- Virus and malware attribution<br>- Threat modeling & threat event categorizations<br>- Insider threat Attribute development<br>- Threat Intel Integration with Risk Management program<br>- Integrates data insights with data science, BI, and analytics across HR, legal, IT, and security teams | - Maintains Microsoft Defender for Identity threat modeling<br>- Maintains Microsoft Defender for Office 365 threat modeling<br>- Maintains Microsoft Defender for Endpoint threat modeling |
| Monitoring | - Tier 1, 2, 3 analysts<br>- Log source maintenance and engineering<br>- Data source ingestion<br>- SIEM parsing, alerting, correlation, optimization<br>- Event and alert generation<br>- Event and alert analysis<br>- Event and alert reporting<br>- Ticketing system maintenance | Uses:<br><br>- Security & Compliance Center<br>- Microsoft Defender portal |
| Engineering & SecOps | - Vulnerability management for apps, systems, and endpoints<br>- XDR/SOAR automation<br>- Compliance testing<br>- Phishing and DLP engineering<br>- Engineering<br>- Coordinates change control<br>- Coordinates runbook updates<br>- Penetration testing | - Microsoft Defender for Cloud Apps<br>- Defender for Endpoint<br>- Defender for Identity |
| Computer Security Incident Response Team \(CSIRT\) | - Investigates and responds to cyber incidents<br>- Performs forensics<br>- **May often be isolated from SOC** | Collaborate and maintain Microsoft Defender XDR incident response playbooks |
|  |  |  |

## Next step

Continue with [Develop and test use cases](https://learn.microsoft.com/en-us/defender-xdr/integrate-microsoft-365-defender-secops-use-cases).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
