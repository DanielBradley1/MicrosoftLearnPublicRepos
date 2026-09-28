<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/security/standard-security-threat-protection -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 4: Microsoft threat protection

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

This article explores the various Microsoft security threat protection features available for educational institutions with a Microsoft 365 A3 license. These features are designed to help protect sensitive information, ensure compliance with data protection regulations, and provide a secure learning environment for students and staff.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Microsoft Defender

| Feature | Description | Learn more Links |
| --- | --- | --- |
| **Windows Defender Antivirus** | Brings together machine learning, big data analysis, and threat resistance for Windows | [Microsoft Defender Antivirus in Windows](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) |
| **Cloud Protection** | Works in tandem with local antivirus protections, enabling enhancing real-time protection | [Cloud protection and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/cloud-protection-microsoft-defender-antivirus) |
| **Tamper Protection** | Blocks disabling security features and antivirus | [Protect security settings with tamper protection](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection) |
| **Block at first sight** | Detects new malware and blocks within seconds | [Enable block at first sight to detect malware in seconds](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-block-at-first-sight-microsoft-defender-antivirus) |
| **Block Unwanted Apps** | Block Potentially Unwanted Apps \(PUAs\) | [Block potentially unwanted applications with Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) |
| **Always on protection** | Real-time protection, monitoring, and heuristics to identify malware | [Enable and configure Microsoft Defender Antivirus protection capabilities](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |

## Microsoft Defender Firewall

Microsoft Defender Firewall is an essential security feature that helps protect devices and networks from unauthorized access and cyber threats. In an educational setting, it plays a crucial role in safeguarding sensitive information and ensuring a secure learning environment.

**Key features of Microsoft Defender Firewall:**

- **Network protection** blocks unauthorized network traffic and helps prevent cyber attacks by controlling inbound and outbound connections.
- **Integration with Microsoft Defender for Endpoint** provides comprehensive threat detection and response capabilities, enhancing overall security.
- **Customizable rules** allow IT administrators to create and manage firewall rules tailored to the specific needs of the educational institution.

**Benefits in education:**

- **Enhanced security:** Protects student and staff data from cyber threats, ensuring a safe digital environment.
- **Compliance:** Helps schools comply with data protection regulations and policies.
- **Ease of management:** Integrated with Windows, making it easy for IT administrators to deploy and manage across multiple devices.

**To set up Microsoft Defender Firewall:**

- Using Group Policy:

  1. Open the Group Policy Management Console \(GPMC\).
  2. Navigate to **Computer Configuration > Windows Settings > Security Settings > Windows Defender Firewall with Advanced Security**.
  3. Configure inbound and outbound rules as needed.

- Using Microsoft Intune:

  1. Sign in to the Microsoft Endpoint Manager admin center.
  2. Go to **Devices > Configuration profiles > Create profile**.
  3. Select **Windows 10 and later** and **Endpoint protection**.
  4. Configure the firewall settings and assign the profile to the appropriate groups.

- Using PowerShell:

  1. You can also use PowerShell to manage firewall settings. For example, to enable the firewall:  
     `Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True`

**Monitoring and maintenance:**

- **Regular updates:** Ensure that all systems are regularly updated to maintain security.
- **Training:** Educate staff and students on the importance of network security and how to recognize potential threats.
- **Support:** Provide IT support to handle any issues related to the firewall.

**Learn more:**

- [Ensure secure learning experiences with Microsoft Defender for Endpoint P2 – Students](https://www.microsoft.com/education/blog/2024/04/ensure-secure-learning-experiences-with-microsoft-defender-for-endpoint-p2-students/)
- [Ensuring secure, safe experiences for every school](https://www.microsoft.com/education/blog/2023/10/ensuring-secure-safe-experiences-for-every-school/)

## Microsoft Defender Exploit Guard

Microsoft Defender Exploit Guard is a set of security features designed to protect devices and data from various types of attacks. It's useful in educational settings where safeguarding sensitive information is crucial. Here’s how it can be managed and implemented in schools.

**Key features of Microsoft Defender Exploit Guard:**

- **Attack surface reduction** helps minimize the areas where your organization is vulnerable to cyber threats by blocking or auditing specific types of activities and behaviors.
- **Controlled folder access** protects files and folders from unauthorized changes by malware or other threats. Only trusted apps can access protected folders.
- **Exploit protection** provides advanced protections for applications and the operating system to prevent exploits from being used to compromise devices.
- **Network protection** blocks outbound connections from apps to known malicious IP addresses, domains, and URLs.

**Benefits in education:**

- **Enhanced security:** Protects sensitive educational data, such as student records and research data, from being compromised.
- **Compliance:** Helps educational institutions comply with data protection regulations and policies.
- **Ease of management:** Integrated into Windows, making it easier for IT administrators to deploy and manage across multiple devices.

**To set up Microsoft Defender Exploit Guard**:

- Using Group policy:

  1. Open the Group Policy Management Console \(GPMC\).
  2. Navigate to **Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Windows Defender Exploit Guard**.
  3. Configure the settings for each component \(Attack surface reduction, Controlled Folder Access, Exploit Protection, Network Protection\).

- Using Microsoft Intune:

  1. Sign in to the Microsoft Endpoint Manager admin center.
  2. Go to **Devices > Configuration profiles > Create profile**.
  3. Select Windows 10 and later and Endpoint protection.
  4. Configure the Exploit Guard settings and assign the profile to the appropriate groups.

- Using PowerShell:

  1. You can also use PowerShell to configure Exploit Guard settings. For example, to enable attack surface reduction rules:  
     `Set-MpPreference -AttackSurfaceReductionRules_Actions Enabled`

**Monitoring and Maintenance:**

- **Regular Updates:** Ensure that all systems are regularly updated to maintain security.
- **Training**: Educate staff and students on the importance of security and how to recognize potential threats.
- **Support:** Provide IT support to handle any issues related to Exploit Guard.

**Learn more:**

- [Enable exploit protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-exploit-protection)
- [Create and deploy an Exploit Guard policy](https://learn.microsoft.com/en-us/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy)

## Microsoft Defender Credential Guard

Microsoft Defender Credential Guard is a security feature designed to protect credentials in Windows by isolating them in a secure environment. This feature is beneficial in educational settings where protecting sensitive information is crucial.

**Key features of Microsoft Defender Credential Guard:**

- **Credential isolation:** It uses virtualization-based security to isolate secrets so that only privileged system software can access them.
- **Protection against credential theft:** Helps prevent attacks such as Pass-the-Hash and Pass-the-Ticket by ensuring that credentials aren't stored in a way that can be easily accessed by attackers.
- **Integration with Windows Security:** Works seamlessly with other Windows security features to provide comprehensive protection.

**Benefits in education:**

- **Enhanced security:** Protects sensitive information such as student records, staff credentials, and administrative data from being compromised.
- **Compliance:** Helps educational institutions comply with data protection regulations and policies.
- **Ease of management:** Integrated into Windows, making it easier for IT administrators to deploy and manage across multiple devices.

**To set up Microsoft Defender Credential Guard:**

1. Verify your system meets the requirements:

   - Windows 10 Enterprise, Education, or Pro
   - UEFI firmware with Secure Boot
   - Virtualization extensions \(Intel VT-x or AMD-V\)

2. Enable Credential Guard:

   - Using Group Policy:

     1. Open the Group Policy Management Console \(GPMC\).
     2. Navigate to **Computer Configuration > Administrative Templates > System > Device Guard**.
     3. Enable the policy **Turn On Virtualization Based Security**.
     4. Configure the Credential Guard Configuration settings.

   - Using PowerShell: `Enable-WindowsOptionalFeature -Online -FeatureName Windows-Defender-Credential-Guard`

3. Verify Credential Guard:

   - Use the System Information tool to verify that Credential Guard is running:

     1. Open System Information.
     2. Check the Device Guard section for Credential Guard status.

**Monitoring and maintenance:**

- **Regular updates:** Ensure that all systems are regularly updated to maintain security.
- **Training:** Educate staff and students on the importance of credential security and how to recognize potential threats.
- **Support:** Provide IT support to handle any issues related to Credential Guard.

## Microsoft Defender for Endpoint Plan 1 and Plan 2

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help organizations like yours to prevent, detect, investigate, and respond to advanced threats. Microsoft Defender for Endpoint is now available in two plans:

- [**Microsoft Defender for Endpoint Plan 1 \(P1\)**](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1) is ideal for organizations looking for foundational endpoint protection with essential security features. P1 is available with the A3 license.
- [**Defender for Endpoint Plan 2 \(P2\)**](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) is suited for organizations that require comprehensive security solutions with advanced threat detection, investigation, and response capabilities. P2 is available as an addon with A5 license.

### Compare Microsoft Defender for Endpoint Plan 1 versus Plan 2

Here's a feature comparison between Microsoft Defender for Endpoint Plan 1 \(P1\) and Plan 2 \(P2\). A checkmark \(✔️\) means that the plan supports the feature or capability. An X \(❌\) means that the plan doesn't support it.

| **Feature** | **Description** | **Plan 1 \(P1\)** | **Plan 2 \(P2\)** |
| --- | --- | --- | --- |
| **Next-generation protection** | Provides robust antivirus and anti-malware protection using behavior-based, heuristic, and real-time detection methods. | ✔️ | ✔️ |
| **Attack surface reduction** | Helps harden devices against zero-day attacks and offers granular control over endpoint access and behaviors. | ✔️ | ✔️ |
| **Manual response actions** | Allows security teams to take manual actions, such as quarantining files or isolating devices. | ✔️ | ✔️ |
| **Centralized management** | Uses the Microsoft Defender portal for viewing incidents, managing devices, and generating reports on detected threats. | ✔️ | ✔️ |
| **Cross-platform support** | Supports Windows, macOS, iOS, and Android devices. | ✔️ | ✔️ |
| **Endpoint detection and response \(EDR\)** | Detects, investigates, and responds to advanced threats that bypassed initial defenses. | ❌ | ✔️ |
| **Automated investigation and remediation** | Reduces the volume of alerts by automatically investigating and remediating threats at scale. | ❌ | ✔️ |
| **Threat and vulnerability management** | Provides insights into vulnerabilities and misconfigurations across your environment. | ❌ | ✔️ |
| **Advanced threat hunting** | Allows security teams to proactively hunt for threats using advanced tools. | ❌ | ✔️ |
| **Threat intelligence** | Uses Microsoft's extensive threat intelligence network to identify attacker tools, techniques, and procedures. | ❌ | ✔️ |
| **Sandboxing** | Isolates and analyzes potentially malicious files in a secure environment. | ❌ | ✔️ |
| **Managed threat hunting service** | Offers expert threat hunting services to help identify and mitigate threats. | ❌ | ✔️ |
| **Microsoft Secure Score for devices** | Provides a security score to help you understand and improve your security posture. | ❌ | ✔️ |

**Learn more:**

- [Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Ensure secure learning experiences with Microsoft Defender for Endpoint P2 – Students](https://www.microsoft.com/education/blog/2024/04/ensure-secure-learning-experiences-with-microsoft-defender-for-endpoint-p2-students/)

## Microsoft Advanced Threat Analytics

Microsoft Advanced Threat Analytics \(ATA\) is an on-premises cybersecurity solution designed to detect and investigate advanced threats, compromised identities, and insider actions within enterprise networks. While it isn't actively included in current Microsoft 365 Education plans, understanding its capabilities can still be relevant for legacy deployments or institutions with hybrid environments.

**What ATA Does:**

ATA uses a proprietary network parsing engine to analyze traffic from protocols like Kerberos, DNS, RPC, and NTLM. It builds behavioral profiles of users and devices by collecting data from:

- Port mirroring on domain controllers and DNS servers
- Lightweight Gateways installed directly on domain controllers
- Windows Event Forwarding \(WEF\)
- SIEM integrations

It detects threats across three main categories

- Malicious attacks \(for example, Pass-the-Ticket, Pass-the-Hash, Golden Ticket, brute force, reconnaissance\)
- Abnormal behavior \(for example, unusual logins or lateral movement\)
- Security issues and risks \(for example, credential exposure or misconfigurations\)

ATA presents findings in a user-friendly dashboard that highlights the "who, what, when, and how" of suspicious activities.

**Relevance in education:**

Although ATA isn't part of Microsoft 365 Education A1, A3, or A5 plans, it may still be used in:

- Hybrid environments where on-premises Active Directory is in use
- Higher education institutions with legacy infrastructure or specific compliance needs
- Research networks requiring deep packet inspection and behavioral analytics ATA can help protect sensitive academic data, student records, and research IP from internal and external threats.

**Support lifecycle and transition:**

- Mainstream support for ATA ended in January 2021.
- Extended support continues until January 2026.

Microsoft recommends transitioning to cloud-native solutions like:

- Microsoft Defender for Identity \(formerly Azure ATP\)
- Microsoft Defender XDR
- Microsoft Sentinel for SIEM/SOAR capabilities

## Microsoft Defender AntiMalware

Microsoft Defender Antimalware is a core component of the Microsoft 365 Education security suite, designed to protect schools and educational institutions from a wide range of cyber threats. Here's a comprehensive overview tailored to the education context, based on internal communications, Microsoft Learn documentation, and public education-focused guidance.

**What it is:**

Microsoft Defender Antimalware is the built-in antivirus and antimalware engine in Windows 10 and 11, including Education and Pro Education editions. It provides:

- Real-time protection against viruses, ransomware, spyware, and other malicious software.
- Cloud-delivered intelligence to detect emerging threats.
- Daily quick scans and on-demand full scans to ensure endpoint hygiene.

**How it works in education:**

- Protect student and faculty devices from malware, especially in 1:1 device programs.
- Prevent ransomware attacks that could compromise sensitive student data or disrupt learning.
- Support compliance with regulations like FERPA and COPPA by safeguarding personal information.

It integrates seamlessly with:

- Microsoft Intune for Education for policy deployment and device management.
- Microsoft Defender for Endpoint for advanced threat detection and response.
- Microsoft 365 A5 Education plans, which unify identity, data, and device protection.

**Key features:**

| Feature | Description |
| --- | --- |
| Real-time protection | Monitors devices continuously for malicious activity |
| Heuristic and signature-based detection | Identifies both known and unknown threats |
| Tamper protection | Prevents unauthorized changes to security settings |
| Firewall integration | Works with Windows Firewall to block suspicious traffic |
| Cross-platform support | Available on Windows, macOS, and Android |

**Deployment in schools:**

Microsoft Defender Antimalware is included in:

- Windows 10/11 Education and Pro Education
- Microsoft 365 A3 and A5 Education plans
- Microsoft Defender for Endpoint onboarding, which enhances its capabilities with endpoint detection and response \(EDR\).

Schools can manage Defender policies using:

- Group Policy or MDM \(for example, Intune\)
- ADMX-backed CSPs for granular control over Defender settings

**Why it matters:**

Cyberattacks on schools are increasing in frequency and sophistication. Defender Antimalware helps:

- Reduce reliance on third-party antivirus tools, simplifying IT management.
- Lower total cost of ownership by consolidating security tools under Microsoft 365 A5.
- Improve response time to threats with centralized visibility and automation

## Microsoft Defender AntiVirus

Microsoft Defender Antivirus is a foundational security solution built into Windows 10 and 11 Education editions, designed to protect students, educators, and school systems from malware, ransomware, and other cyber threats. Here's a breakdown of how it functions in educational environments, based on internal communications, Microsoft Learn documentation, and public education-focused guidance.

**What it is:**

Microsoft Defender Antivirus is the default antimalware engine in Windows, offering:

- Real-time protection against viruses, spyware, and ransomware.
- Cloud-delivered intelligence to detect emerging threats.
- Daily quick scans and on-demand full scans to ensure endpoint hygiene. It's tightly integrated with Microsoft Defender for Endpoint, which provides advanced threat detection, attack surface reduction, and endpoint response capabilities.

**Key capabilities in education:**

- **Device protection for students and staff:** Defender Antivirus helps secure devices used in classrooms, labs, and remote learning environments. It blocks malicious files, phishing attempts, and suspicious behaviors before they can compromise systems.
- **Cloud-based threat intelligence:** Defender uses Microsoft’s global threat intelligence network to detect and respond to new threats in real time. This is especially important in education, where devices are often shared or used off-campus.
- **Policy management via Intune for Education:** IT admins can configure Defender policies using Microsoft Intune, ensuring consistent protection across all devices. This includes setting cloud protection levels, scan schedules, and tamper protection.
- **Integration with Microsoft 365 A5 Security:** Defender Antivirus is a core component of Microsoft 365 A5 for Education, which unifies identity, data, and device protection. It works alongside Defender for Identity, Defender for Office 365, and Defender for Endpoint to provide layered security.

**Advanced features:**

| Feature | Description |
| --- | --- |
| CloudBlockLevel | Controls how aggressively Defender blocks suspicious files. Options range from default to zero-tolerance |
| Health monitoring | Reports device health status, including pending scans, reboots, or critical failures |
| Security intelligence Updates | Defender receives frequent updates to stay ahead of evolving threats |
| Passive mode support | If another antivirus is active, Defender can run in passive mode to support Defender for Endpoint |

**Why it matters for schools:**

Education is one of the most targeted sectors for cyberattacks, with nearly 80% of malware encounters occurring in this space. Microsoft Defender Antivirus helps:

- Protect sensitive student and staff data
- Maintain compliance with regulations like FERPA and COPPA
- Reduce IT overhead by automating threat detection and response.
