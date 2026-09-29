<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/connectors-detect-respond-to-compromise -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Respond to a compromised connector

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Connectors are used for enabling mail flow between Microsoft 365 and email servers that you have in your on-premises environment. For more information, see [Configure mail flow using connectors in Exchange Online](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

An inbound connector with the **Type** value `OnPremises` is considered compromised when an attacker creates a new connector or modifies and existing connector to send spam or phishing email.

This article explains the symptoms of a compromised connector and how to regain control of the connector.

## Symptoms of a compromised connector

A compromised connector exhibits one or more of the following characteristics:

- A sudden spike in outbound mail volume.
- A mismatch between the `5321.MailFrom` address \(also known as the **MAIL FROM** address, P1 sender, or envelope sender\) and the `5322.From` address \(also known as the From address or P2 sender\) in outbound email. For more information about these senders, see [How Microsoft 365 validates the From address to prevent phishing](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-from-email-address-validation#an-overview-of-email-message-standards).
- Outbound mail sent from a domain that isn't provisioned or registered.
- The connector is blocked from sending or relaying mail.
- The presence of an inbound connector that wasn't created by an admin.
- Unauthorized changes in the configuration of an existing connector \(for example, the name, domain name, and IP address\).
- A recently compromised admin account. Creating or editing connectors requires admin access.

If you see any of the preceding signs of connector compromise or other unusual symptoms, you should investigate.

## Secure and restore email function to a suspected compromised connector

Do **all** of the following steps to regain control of a compromised inbound connector. Go through the steps as soon as you suspect a problem and as quickly as possible to make sure that the attacker doesn't resume control of the connector. These steps also help you remove any back-door entries that the attacker might have added to the connector.

### Step 1: Identify if an inbound connector has been compromised

To confirm whether a connector is compromised, [review recent suspicious connector traffic or related messages](#review-recent-suspicious-connector-traffic-or-related-messages) and [investigate and validate connector-related activity](#investigate-and-validate-connector-related-activity).

#### Review recent suspicious connector traffic or related messages

Tip

The Explorer view in the following procedure requires [Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about). If you don't have Plan 2, skip to the **Alerts** and **Message trace** procedure later in this section.

In [Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about), open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com) and go to **Explorer**. Or, to go directly to the **Explorer** page, use [https://security.microsoft.com/threatexplorer](https://security.microsoft.com/threatexplorer).

1. On the **Explorer** page, verify that the **All email** tab is selected and then configure the following options:

   - Select the date/time range.
   - Select **Connector**.
   - Enter the connector name in the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-search.png) **Search** box.
   - Select **Refresh**.


   [![Inbound connector explorer view](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-explorer.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-explorer.png#lightbox)

2. Look for abnormal spikes or dips in email traffic.

   [![Number of emails delivered to junk folder](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-abnormal-spike.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-abnormal-spike.png#lightbox)
3. Answer the following questions:

   - Does the **Sender IP** match your organization's on-premises IP address?
   - Were a significant number of recent messages sent to the **Junk Email** folder? This result clearly indicates that a compromised connector was used to send spam.
   - Is it reasonable for the message recipients to receive email from senders in your organization?


   [![Sender IP and your organization's on-prem IP address](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-sender-ip.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-sender-ip.png#lightbox)

In [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) or [the built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about), use **Alerts** and **Message trace** to look for the symptoms of connector compromise:

1. Open the Defender portal at [https://security.microsoft.com](https://security.microsoft.com) and go to **Incidents & alerts** > **Alerts**. Or, to go directly to the **Alerts** page, use [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts).
2. On the **Alerts** page, use the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-filter.png) **Filter** > **Policy** > **Suspicious connector activity** to find any alerts related to suspicious connector activity.
3. Select a suspicious connector activity alert by clicking anywhere in the row other than the check box next to the name. On the details page that opens, select an activity under **Activity list**, and copy the **Connector domain** and **IP address** values from the alert.

   [![Connector compromise outbound email details](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-outbound-email-details.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-outbound-email-details.png#lightbox)
4. Open the Exchange admin center at [https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com) and go to **Mail flow** > **Message trace**. Or, to go directly to the **Message trace** page, use [https://admin.exchange.microsoft.com/#/messagetrace](https://admin.exchange.microsoft.com/#/messagetrace).

   On the **Message trace** page, select the **Custom queries** tab, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Start a trace**, and use the **Connector domain** and **IP address** values from the previous step.

   For more information about message trace, see [Message trace in the modern Exchange admin center in Exchange Online](https://learn.microsoft.com/en-us/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

   [![New message trace flyout](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-new-message-trace.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-new-message-trace.png#lightbox)
5. In the message trace results, look for the following information:

   - A significant number of messages were recently marked as **FilteredAsSpam**. This result clearly indicates that a compromised connector was used to send spam.
   - Whether it's reasonable for the message recipients to receive email from senders in your organization


   [![New message trace search results](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-message-trace-results.png)](https://learn.microsoft.com/en-us/defender-office-365/media/connector-compromise-message-trace-results.png#lightbox)

#### Investigate and validate connector-related activity

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), replace <StartDate> and <EndDate> with your values, and then run the following command to search the audit log for inbound connector creation, modification, and removal events. For more information, see [Use a PowerShell script to search the audit log](https://learn.microsoft.com/en-us/purview/audit-log-search-script).

```powershell
Search-UnifiedAuditLog -StartDate "<StartDate>" -EndDate "<EndDate>" -Operations "New-InboundConnector","Set-InboundConnector","Remove-InboundConnector"
```

For detailed syntax and parameter information, see [Search-UnifiedAuditLog](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/search-unifiedauditlog).

### Step 2: Review and revert unauthorized change\(s\) in a connector

Open the Exchange admin center at [https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com) and go to **Mail flow** > **Connectors**. Or, to go directly to the **Connectors** page, use [https://admin.exchange.microsoft.com/#/connectors](https://admin.exchange.microsoft.com/#/connectors).

On the **Connectors** page, review the list of connectors. Remove or turn off any unknown connectors, and check each connector for unauthorized configuration changes.

### Step 3: Unblock the connector to re-enable mail flow

After you've regained control of the compromised connector, unblock the connector on the **Restricted entities** page in the Defender portal. For instructions, see [Remove blocked connectors from the Restricted entities page](https://learn.microsoft.com/en-us/defender-office-365/connectors-remove-blocked).

### Step 4: Investigate and remediate potentially compromised admin accounts

After you identify the admin account that was responsible for the unauthorized connector configuration activity, investigate the admin account for compromise. For instructions, see [Responding to a Compromised Email Account](https://learn.microsoft.com/en-us/defender-office-365/responding-to-a-compromised-email-account).

## Related content

For more information about compromised connectors and restricted users, see the following articles:

- [Remove blocked connectors](https://learn.microsoft.com/en-us/defender-office-365/connectors-remove-blocked)
- [Remove blocked users](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-restore-restricted-users)
