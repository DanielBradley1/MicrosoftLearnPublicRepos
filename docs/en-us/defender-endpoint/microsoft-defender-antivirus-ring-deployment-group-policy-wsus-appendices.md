<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-wsus-appendices -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Appendices for Microsoft Defender Antivirus ring deployment using Group Policy and Windows Server Update Services \(WSUS\)

This article provides supplemental information about security intelligence updates, engine updates, and platform updates for the Microsoft Defender Antivirus ring deployment using Group Policy and Windows Server Update Services \(WSUS\).

## Prerequisites

### Supported operating systems

- Windows
- Windows Server

## Appendix A - Security Intelligence Updates

Microsoft continually updates security intelligence in antimalware products to cover the latest threats and to constantly tweak detection logic. The updates enhance the ability of Microsoft Defender Antivirus and other Microsoft antimalware solutions to accurately identify threats. This security intelligence works directly with cloud-based protection to deliver fast and powerful AI-enhanced, next-generation protection.

### References

- [Security intelligence updates for Microsoft Defender Antivirus and other Microsoft antimalware](https://www.microsoft.com/wdsi/defenderupdates)

## Appendix B - Engine Updates

Engine updates are updates for the scan engine that's used by security intelligence updates. The scan engine was first released on July 15, 2010.

## Appendix C - Platform Updates

Platform updates are the .exe, .dll, and .sys files for the Microsoft Defender Antivirus service.

| Channel | Version | Revision | Remarks |
| --- | --- | --- | --- |
| **Beta Channel - Prerelease** | 4.18.2304.4 | '23 April, minor rev 4 | This channel is the one you want to test for app compatibility, reliability, and performance. |
| **Current Channel \(Preview\)** | 4.18.2303.8 | '23 Mar, minor rev 8 | Same as for *Beta Channel - Prerelease*. |
| **Current Channel \(Staged\)** | 4.18.2303.7 | '23 Mar, minor rev 7 | Same as for *Beta Channel - Prerelease*. |
| **Current Channel \(Broad\)** | 4.18.2302.7  <br>see note | '23 Feb, minor rev 7 | This channel is the one you want to push out to 90%-100% of your production systems. |

Note

Where **23** == *2023*, **02** == *February*, and **.7** is the *minor revision*.

## Related content

[Microsoft Defender Antivirus pilot ring deployment using Group Policy and Windows Server Update Services](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-pilot-ring-deployment-group-policy-wsus)
