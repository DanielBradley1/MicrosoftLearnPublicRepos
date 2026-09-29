<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/anti-spam-backscatter-about -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# Backscatter in cloud organizations

*Backscatter* is non-delivery reports \(also known as NDRs or bounce messages\) that you receive for messages you didn't send. Spammers often use real email addresses as the From address to lend credibility to their messages. When a nonexistent recipient receives spam, the destination email server unwittingly sends the NDR to the forged sender in the From address \(also known as the `5322.From` address or P2 sender\).

Microsoft 365 makes every effort to identify and silently drop messages from dubious sources without generating an NDR. But, it's almost impossible for Microsoft 365 to send absolutely no backscatter, based on the sheer volume email flowing through the service.

Backscatterer.org maintains a blocklist \(also known as a DNS blocklist or DNSBL\) of email servers that are responsible for sending backscatter. Their blocklist isn't a list of spammers, and Microsoft 365 servers might appear on their list.

Tip

The Backscatterer.org website \([http://www.backscatterer.org/?target=usage](http://www.backscatterer.org/?target=usage)\) recommends using their service in Safe mode as large email services almost always send some backscatter.

The Advanced Spam Filter \(ASF\) in anti-spam policies has a setting to mark backscatter as spam, but this setting isn't required in most environments. For more information, see [ASF 'mark as spam' settings](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-asf-settings-about#mark-as-spam-settings).
