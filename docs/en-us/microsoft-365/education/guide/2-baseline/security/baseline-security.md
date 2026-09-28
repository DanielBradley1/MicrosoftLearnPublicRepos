<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/security/baseline-security -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 1: Baseline security instructions for education organizations

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft offers a variety of protection and security features out of the box with Microsoft 365 Education tenants. This article details many features immediately available to and recommended for education customers running Microsoft 365 for Education.

## Baseline overview

While Microsoft 365 A3 licenses are explicitly designed for improving an organization’s security and compliance posture, a multitude of out-of-the-box security features and capabilities are available for all education tenants, including those tenants with just the Office 365 A1 license set. This article details the various security settings and configurations recommended by Microsoft for all education customers, as a baseline set of protections for all users on the platform. Once these protections are enabled, Microsoft recommends carefully considering the various security upgrades available through the Microsoft 365 A3 and Microsoft 365 A5 licenses.

## Prerequisites

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/license/a1.png) Microsoft 365 A1 for devices

## Roles and responsibilities

- IT Admin
- Identity Admin
- EXO Admin
- OneDrive Admin
- SharePoint Admin

## Malware protection

Education customers receive more malware attacks than any other industry globally. Protecting your organization from malware is one of the most critical security features Microsoft 365 education admins should enable first. To enable Anti-Malware policies in Exchange Online Protection \(EOP\), follow the instructions in [this link](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-policies-configure). Once enabled, EOP can prevent a variety of malware, ransomware, and spyware attacks from messages and attachments in Exchange Online. [Learn More.](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-malware-protection-about)

Note

For education scenarios: Education is the most attacked industry globally for malware, and the need for protection has never been greater. EDU needs the ability to prevent and stop malware compromises which can lead to mass data breaches, costly tech platform shutdowns, and unexpected student harm overall.

## Spam protection

In the modern world of buying and selling personal information for ads and malicious attacks, preventing spam is a critical feature to prevent end users from receiving endless unsolicited mail and impeding their productivity and ability to focus on what matters most. Microsoft recommends all education customers [enable anti-spam protection in EOP.](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure). Policies can be configured to adjust your spam filter based on the admin defined spam confidence level \(SCL\) to ensure you're filtering the right amount of mail from the organization. Once enabled, users are protected from externally generated spam campaigns for advertisements and malicious purposes in Exchange Online. [Learn More.](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/eop-about)

Note

For education scenarios: Protecting against Spam in Education can obviously help avoid what is a perceived nuisance, but some education institutions have requirements and laws which prevent advertising to students. Some spam campaigns can contain malicious and harmful content, completely inappropriate for kids and dangerous for the organization. Protecting against spam in education is a critical protection to employ as part of your overall security posture and student protections.

## Phishing protection

The most common method of compromising personal data is phishing, where attackers send unsolicited emails containing malicious links to end users, hoping they engage and compromise themselves. In education, users can be vulnerable due to student populations who never received anti-phishing training. This fact strengthens the need and value for out of the box phishing protection, which is provided for all Microsoft 365 Education tenants in EOP. To enable anti-phishing policies in EOP, follow the instructions in [this link](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about). Once enabled, admins are able to mitigate and automatically block emails associated with phishing as they're sent into the organization, before end users can compromise themselves, their devices, their personal information, and any information they might have access to across the organization. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-phishing-policies-eop-configure)

Note

For education scenarios: It can be incredibly difficult to train students in K12 to identify phishing attempts, so having a systematic approach is critical for these user populations to stay protected and thwart potential attackers trying to compromise children and often unaware student populations.

## Spoofing prevention and intelligence

In the modern era of digital security, spoofing is a common approach attackers use to hide their true identity and make it appear they're someone else, also known as a forged sender. Spoofing is often used as a complimentary component in phishing attacks. Protection from these spoofing attempts can be enabled within your organization’s anti-phishing policies. Admins also can configure detailed Allow/Block lists to provide even more granular controls over what is blocked or allowed, and EOP provides a [Spoof Detection Insights report](https://learn.microsoft.com/en-us/defender-office-365/anti-spoofing-spoof-intelligence#use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell) to ensure visibility into spoofing attempts made against the organization. [Learn More.](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-spoofing-spoof-intelligence)

Note

For education scenarios: It can be incredibly difficult to train students in K12 to self-identify spoofing attempts, so having a systematic approach is critical for these user populations to stay protected and thwart potential attackers trying to compromise children and often unaware student populations.

## Zero-Hour Auto Purge \(ZAP\)

Zero-day attacks are some of the most malicious and disruptive types of attacks in use today, using the latest exploits discovered \(and sometimes those exploits yet to be discovered\). Zero-day attacks can sometimes bypass the predefined malware, spam, and phishing filters for incoming mail. Links can also initially be sent without any detectable malicious intent and then be updated after they're received to include malware. Because of these methods, the ZAP process attempts to retroactively scan, detect, and neutralize malicious phishing, spam, or malware messages that have already been delivered to your organizations Exchange Online mailboxes within the past 48 hours. ZAP can be enabled within your anti-spam policy and anti-malware policy described previously. [Learn More.](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/zero-hour-auto-purge)

Note

For education scenarios: Zero Days attacks are some of the most significant vectors for attack and compromise, costing education institutions millions of dollars to remediate and recover from. This protection is absolutely critical in maintaining the overall security posture and safety, and mitigating attacks, for both K12 and HED.

## Purview message encryption

Microsoft 365 provides all education users message encryption and rights management capabilities. Microsoft recommends [enabling Purview Message Encryption over the legacy Office 365 Message Encryption \(OME\)](https://learn.microsoft.com/en-us/purview/ome-version-comparison#advantages-of-microsoft-purview-message-encryption-over-legacy-ome) option. The modern approach allows for end user-initiated options such as Do Not Forward, encrypt only, and custom branding, in addition to admin triggered options through mail flow rules. This approach also supports both internal and external recipients, ensuring more holistic protection and coverage. The steps need to enable or verify Purview Message Encryption is enabled, are available in [Set up Microsoft Purview Message Encryption \| Microsoft Learn](https://learn.microsoft.com/en-us/purview/set-up-new-message-encryption-capabilities).

Note

For education scenarios: Message Encryption allows higher education organizations to establish trusted partnerships with other universities and research institutions, by ensuring content is protected and cannot be shared more broadly outside, protecting valuable IP and data along the way.
