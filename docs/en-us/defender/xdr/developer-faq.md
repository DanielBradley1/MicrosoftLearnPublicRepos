<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/developer-faq -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Software developer FAQ

This page provides answers to common questions we receive from software developers. For general guidance about submitting malware or incorrectly detected files, read the submission guide.

## Does Microsoft accept files for a known list or false-positive prevention program?

No. We don't accept these requests from software developers. Developers who signing their program's files in a consistent manner, with a digital certificate issued by a trusted root authority, helps our research team quickly identify the source of a program and apply previously gained knowledge. In some cases, this might result in your program being quickly added to the known list. Far less frequently, it adds your digital certificate to a list of trusted publishers.

## How do I dispute the detection of my program?

Submit the file in question as a software developer. Wait until your submission has a final determination.

If you're not satisfied with our determination of the submission, use the developer contact form provided with the submission results to reach Microsoft. We use the information you provide to investigate further if necessary.

We encourage all software vendors and developers to read about [how Microsoft identifies malware and Potentially Unwanted Applications \(PUA\)](https://learn.microsoft.com/en-us/defender-xdr/criteria).

## Why is Microsoft asking for a copy of my program?

Providing copies can help us with our analysis. Participants of the [Microsoft Active Protection Service \(MAPS\)](https://www.microsoft.com/msrc/mapp) might occasionally receive these requests. The requests stop after our systems have received and processed the file.

## Why does Microsoft classify my installer as a software bundler?

It contains instructions to offer a program classified as unwanted software. You can review the [criteria](https://learn.microsoft.com/en-us/defender-xdr/criteria) we use to check applications for behaviors that are considered unwanted.

## Why is the Windows Firewall blocking my program?

Firewall blocks aren't related to Microsoft Defender Antivirus and other Microsoft antimalware. [Learn about Windows Firewall](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

## Why does the Microsoft Defender SmartScreen say my program isn't commonly downloaded?

Microsoft Defender SmartScreen isn't related to Microsoft Defender Antivirus and other Microsoft antimalware. [Learn about Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)
