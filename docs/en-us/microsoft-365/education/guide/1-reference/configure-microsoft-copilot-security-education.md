<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/configure-microsoft-copilot-security-education -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# Configure Microsoft Copilot security for education

As schools and educational organizations adopt artificial intelligence to enhance learning and streamline operations, protecting sensitive information and ensuring safe technology use are top priorities. This article guides educational IT administrators and leaders through some security and privacy features and configurations for Microsoft Copilot and Copilot Chat to help institutions maintain compliance and foster a secure environment for both educators and students.

## Copilot default protection and safety

Microsoft Copilot is designed with built-in protections that safeguard sensitive information while promoting responsible and compliant use of AI in academic environments. The following list describes some of the default protection and safety features:

- **Security and Data Privacy in Copilot:** Copilot keeps all data encrypted and within the tenant boundary, doesn't use customer data for model training, and maintains compliance with existing Purview data security configurations, addressing concerns about PII exposure.

  - **Secure and encrypted -** Copilot secures and encrypts data at rest and in transit.
  - **Private -** Copilot never uses your data to train foundation models, and keeps your PII safe from corporate use.
  - **Compliant -** Copilot respects your existing Microsoft 365 data permissions and policies - no new data access is granted.
  - **Responsible -** Microsoft is committed to developing AI systems in a transparent, reliable, and trustworthy way.

- **Content Safety and Admin Controls:**

  - Built-in content safety protections against:

    - Adult content - Vulgar content, prostitution, nudity, pornography, abuse, and child exploitation
    - Violence - Weapons, bullying and intimidation, terrorism and extremism, stalking
    - Self-harm - Suicide, eating disorders, bullying and intimidation
    - Hate - Race, ethnicity, nationality, gender identity, sexual orientation, religion, personal appearance

  - Jailbreak detection
  - Admin controls for disabling features like image generation, web search, self-service purchase, and personalization.

- **Advanced Data Security with Purview:** Use Purview features such as Communication Compliance, Data Security Posture Management, and endpoint/browser data loss protection \(DLP\) to monitor and protect sensitive data, especially when integrating Copilot with backend data stores and mitigating risks from third-party AI usage.

Learn more:

- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy)
- [Security for Microsoft Copilot](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-ai-security)
- [Microsoft Copilot Chat Privacy and Protections](https://learn.microsoft.com/en-us/copilot/privacy-and-protections)

## Configure Copilot base admin controls for education

The [Copilot Control System](https://learn.microsoft.com/en-us/copilot/microsoft-365/copilot-control-system/overview) is a framework of integrated controls and capabilities for Microsoft Copilot and agents. Use it to help secure data that Copilot and agents create or reference, manage Copilot and agent experiences, and measure and analyze adoption and impact across your organization.

While this list isn't exhaustive, here are a few important features to consider and configure in an education environment.

- **Disable and block**

  - Disable Copilot Chat \(Integrated Apps\)
  - Block Image Generation
  - Block Web Search
  - Block Self Service Purchase
  - Disable Personalization

- **Modify app experience**

  - Disable in Teams
  - Disable in Teams Meetings
  - Disable in Edge
  - Disable in Office Apps

- **Agent and connectors**

  - Block Agents
  - Block Agent Creation
  - Manage Agent Pinning
  - Enable and Disable Connectors

## Configure Copilot advanced data controls

Purview has a large number of features for data security and compliance. Everything that you configure in Purview correlates back to data protection that you get out of Copilot.

The following features are particularly useful for education scenarios:

- **Communication compliance** - Detect sensitive content within Copilot and alert admins
- **Data Security Posture Management \(DSPM\)** - Detect third-party and consumer AI usage across the organization
- **Endpoint DLP and Browser DLP** - Detect and block sensitive content being uploaded to third-party AIs

### Communication compliance

Purview can monitor and alert on any activity that happens within Copilot Chat or Microsoft Copilot. When you enable [Communication Compliance](https://learn.microsoft.com/en-us/purview/communication-compliance), admins receive alerts for any sensitive content \(for example, if a user searches for content in the realm of a self-harm category or anything that violates school policy\) in the Purview dashboard. Communication compliance is highly configurable:

- Use a basic keyword block list.
- Use the prebuilt templates or sensitive information types \(SITs\) in Purview.
- Create your own trainable classifier so you can develop one based on the school's policy.

### Data Security Posture Management \(DSPM\)

You want to both monitor and protect data from entering third-party AIs. [**Data Security Posture Management**](https://learn.microsoft.com/en-us/purview/data-security-posture-management) is a feature in Purview that allows you to track and monitor all third-party AI usage across your entire organization. After you set up the DSPM in the portal, you can see what third-party AIs are being used and then take whatever necessary steps, such as a web content filtering block policy, network configuration, or disabling particular apps.

### Endpoint DLP and Browser DLP

If you want to allow third-party AIs, you need to protect your most sensitive data. [Endpoint DLP and Browser DLP](https://learn.microsoft.com/en-us/purview/endpoint-dlp-getting-started) allow you to block the upload and copying of sensitive data elements that Purview identifies within your tenant, SharePoint, OneDrive, or anywhere within your organizational data stores, and prevent that data from being uploaded into those third-party consumer AIs.
