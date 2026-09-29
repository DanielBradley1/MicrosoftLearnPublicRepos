<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-demonstration-smartscreen-url-reputation -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# URL reputation demonstrations

Test how Microsoft Defender SmartScreen helps you identify phishing and malware websites based on URL reputation.

## Prerequisites

- Client devices must be running Windows 11 or Windows 10
- Server devices must be running Windows Server 2008 R2 SP1, Windows Server 2012 R2 and later, or Azure Stack HCI OS, version 23H2 and later.
- Microsoft Edge browser required
- For more information, see [Microsoft Defender SmartScreen](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/)

## SmartScreen for Microsoft Edge URL scenario demonstrations

### Is This Phishing?

Alerts the user to a suspicious page and ask for feedback:

- [Is this Phishing?](https://demo.smartscreen.msft.net/other/areyousure.html)

  Launching this link should render a message similar to the following screenshot:

  ![SmartScreen alerts the user the site is potentially a phishing site and possibly unsafe](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-url-reputation-is-this-phishing.png)

### Phishing Page

A page known for phishing that should be blocked:

- [A known Phishing page](https://demo.smartscreen.msft.net/phishingdemo.html)

  Launching this link should render a message similar to the following example:

  ![SmartScreen reports the site is known for containing phishing threats](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-url-reputation-this-is-phishing.png)

### Malware page

A page that hosts malware and should be blocked:

- [A known malware page](https://demo.smartscreen.msft.net/other/malware.html)

  Launching this link should render a message similar to the following screenshot:

  ![SmartScreen alerts the user that the site is know for containing harmful programs](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-url-reputation-malware-page.png)

### Blocked download

Blocked from downloading because of its URL reputation

- [Download blocked due to URL reputation](https://demo.smartscreen.msft.net/download/malwaredemo/freevideo.exe)

  Launching this link should render a warning that the download was blocked as being unsafe by Microsoft Edge.

### Exploit page

A page that attacks a browser vulnerability

- [Known browser exploit page](https://demo.smartscreen.msft.net/other/exploit.html)

  Launching this link should render a message similar to the Malware page message.

### Malvertising

A benign page hosting a malicious advertisement

- [A page known to contain malicious advertisements](https://demo.smartscreen.msft.net/other/exploit_frame.html)

  Launching this link should render a message similar to the following screenshot:

  ![A demonstration of how SmartScreen responds to a frame on a page that is detected to be malicious. Only the malicious frame is blocked](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-url-reputation-malvertising.png)

## See also

[Microsoft Defender SmartScreen Documentation](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/)

[Microsoft Defender for Endpoint - demonstration scenarios](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-demonstrations)
