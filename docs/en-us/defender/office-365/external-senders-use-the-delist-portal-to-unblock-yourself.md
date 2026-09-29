<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/external-senders-use-the-delist-portal-to-unblock-yourself -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# External senders - Use the delist portal to remove yourself from the blocked senders list and address 5.7.511 Access denied errors

As an email sender from outside Microsoft 365, are you getting an **Access denied** error message when you try to send email to recipients in Microsoft 365? If your legitimate email is blocked, you can use the procedures in this article to remove the block and allow your mail to be delivered to Microsoft 365 recipients.

Tip

There are good reasons for senders to wind up on the blocked senders list, but mistakes can happen. Take a look at this video for a balanced explanation of blocked senders and delisting:

<iframe src="https://learn-video.azurefd.net/vod/player?id=74e1b7cf-3d15-4b69-b201-7b9220406244" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

> For more information about best practices for sending messages to Microsoft 365, see the following articles:
> 
> - [External senders - Troubleshoot email sent to Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/external-senders-mail-flow-troubleshooting)
> - [Reference: Policies, practices, and guidelines](https://learn.microsoft.com/en-us/defender-office-365/external-senders-policies-practices-guidelines)
> - [How to avoid email authentication failures when sending mail to Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about#how-to-avoid-email-authentication-failures-when-sending-mail-to-microsoft-365)

Microsoft 365 uses a *blocked senders list* to protect customers from spam, spoofing, and phishing attacks. If a source IP address is identified as a potential threat to the service, the message source is added to the blocked senders list to prevent email communication between the source and Microsoft 365 organizations.

If your message to a Microsoft 365 recipient is returned in a non-delivery report \(also known as an NDR or bounce message\) that looks like this, you're on the blocked senders list:

> 550 5.7.606-649 Access denied, banned sending IP \[*Source IP address*\]: To request removal from this list please visit [https://sender.office.com/](https://sender.office.com/) and follow the directions. For more information, see [Email non-delivery reports in Exchange Online](https://learn.microsoft.com/en-us/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

For these delivery failures, we provide the **Office 365 Anti-Spam IP Delist Portal** page at [https://sender.office.com](https://sender.office.com) for external message senders to request their removal from the blocked senders list.

## Use the delist portal to remove yourself from the blocked senders list

Tip

If you receive the error **5.7.511** go to the [How to fix error code 5.7.511](#how-to-fix-error-code-57511) section. You can't use the delist portal to fix yourself.

1. Go to the **Office 365 Anti-Spam IP Delist Portal** page at [https://sender.office.com](https://sender.office.com).
2. Follow the instructions on the page. Use the email address that received the NDR, and the IP address that was specified in the error message. You can enter only one email address and one IP address per visit.
3. When you're finished on the page, select **Submit**.
4. A message that looks like the following example is sent to the email address that you entered on the **Office 365 Anti-Spam IP Delist Portal** page.

   [![The email received when you submit a request through the delist portal](https://learn.microsoft.com/en-us/defender-office-365/media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)](https://learn.microsoft.com/en-us/defender-office-365/media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png#lightbox)

   To return to the delist portal, select the confirmation link in the email message.
5. In the delist portal, select **Delist IP**.

After the IP address is removed from the blocked senders list, email messages that pass [the built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about) and [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) \(including [composite authentication](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about#composite-authentication)\) are delivered to Microsoft 365 recipients. Verify that messages aren't abusive or malicious. Otherwise, the IP address might be blocked again.

Note

Results can vary widely before the restrictions are removed. It might take up to 24 hours or longer.

### How to fix error code 5.7.511

In some scenarios, we might need to conduct other investigations on email traffic from your blocked source IP address. If your message is returned in an NDR with code **5.7.511**, you can't use the delist portal as described earlier in this article. For example:

> 550 5.7.511 Access denied, banned sender\[xxx.xxx.xxx.xxx\]. To request removal from this list, forward this message to `delist@microsoft.com`. For more information, go to [https://go.microsoft.com/fwlink/?LinkId=526653](https://go.microsoft.com/fwlink/?LinkId=526653).

As described in the NDR, send a message to `delist@microsoft.com` to unblock your email source. Include the full NDR code and IP address. Microsoft will contact you within 48 hours with the next steps.

## More information

The delisting form for **Outlook.com, the consumer service** can be found [here](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Be sure to read the [FAQ](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) first for *submission* direction.
