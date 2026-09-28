<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/setup/create-signatures-and-disclaimers?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Create organization-wide email signatures and disclaimers

Create organization-wide email signatures in Microsoft 365 to ensure consistent branding and legal compliance across all outgoing messages. You can set up email signatures to apply to all messages or specific messages based on conditions like recipient or content patterns. This guide shows you how to create and manage these signatures using the Exchange admin center.

## Create a signature that applies to all messages

To learn how to [Create a company-wide email signature](https://go.microsoft.com/fwlink/?linkid=2198031), watch the following video.

<iframe src="https://learn-video.azurefd.net/vod/player?id=e160f7ee-fac5-4dde-8d16-3de01fcc45a5" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Organization-wide signatures are called **disclaimers**, regardless of what they include. For example, they can just be a signature, or they can also include your address, legal disclaimer, or other information.

To create a signature that applies to all messages, follow these steps:

1. Sign in to the [Exchange admin center](https://admin.exchange.microsoft.com/#/).

   Tip

   You can also get to the Exchange admin center from the Microsoft 365 admin center. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/) and then from the left navigation bar, select **… Show all**. Under **Admin centers**, select **Exchange**.
2. From the left navigation bar, select **Mail flow** to expand it.
3. Under **Mail flow**, select **Rules**.
4. In the **Rules** page, select **+ Add a rule**, and then select **Apply disclaimers**.
5. In the **Select rule conditions** page in the **New transport rule** pane:

   1. In the **Name** field, enter a name for the rule.
   2. Select the **Apply this rule** drop-down menu and then select **Apply to all messages**.
   3. Select the **Do the following** drop-down menus and select **Apply a disclaimer to the message** in the left menu and **append a disclaimer** in the right menu.
   4. Under the **Do the following** drop-down menu:

      1. Select the **Enter text** link. In the **specify disclaimer text** pane that opens, enter the text of your disclaimer, and then select **Save**.
      2. Select the **Select one** link. In the **specify fallback option** pane that opens, select **Wrap**, and then select **Save**. This option only applies if the disclaimer can't be added because of encryption or other mail setting that blocks the signature. When **Wrap** is selected, the signature is wrapped in a message envelope.

   5. If desired, select the **Except if** drop-down menus, and then choose whether you want an exception for one of the listed items in the left menu and the condition in the right menu.
   6. Select **Next**.

6. In the **Set rule settings** page in the **New transport rule** pane:

   1. Under **Rule mode**, select **Enforce** to turn on the disclaimer immediately. To test the disclaimer first, select either **Test with Policy Tips** or **Test without Policy Tips** instead.
   2. Select a severity level in the **Severity** drop-down menu.
   3. Select **Activate this rule on** and specify a date to activate the rule.
   4. If desired, select **Deactivate this rule on** and specify a date to deactivate the rule.
   5. If desired, select **Stop processing more rules**. Select this check box to avoid applying additional rules after this rule processes a message.
   6. If desired, select **Defer the message if rule processing doesn't complete**. Select this check box to resubmit the message for processing. By default, the rule is ignored, and delivery of the message continues as normal.
   7. For the **Match sender address in message** drop-down menu, leave it at the default of **Header**. This option isn't relevant in this scenario since the rule applies to all messages.
   8. Select **Next**.

7. In the **Review and finish** page in the **New transport rule** pane, review the settings for the new rule, and then select **Finish**.
8. When the rule finishes saving, select **Done**.

## Limitations of organization-wide email signatures

The following limitations are limitations when managing email signatures in Microsoft 365:

- You can't insert the signature directly under the latest email reply or forward.
- Users can't see server-side email signatures in their **Sent Items** folders.
- You can't embed images in email signatures.
- Rules skip lines that contain variables they can't update. For example, if you use a variable for a user's phone number but the phone number isn't provided for a user, the system skips the line containing the variable.

Tip

Some of these limitations can be overcome by using non-Microsoft tools. To find tools that add capabilities and help manage email signatures and disclaimers, search for `email signature software`. Several of these tools are from Microsoft Gold Partners.

## More resources

For information about organization-wide message disclaimers and signatures, including using PowerShell to add a disclaimer or signature, see [Organization-wide message disclaimers, signatures, footers, or headers in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

## Related content

- [Complete training series for small businesses and users who are new to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/business-video/?view=o365-worldwide)
- [Migrate email and contacts to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/migrate-email-and-contacts-admin?view=o365-worldwide)
- [User email settings](https://learn.microsoft.com/en-us/microsoft-365/admin/email/office-365-user-email-settings?view=o365-worldwide)
- [Overview of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide)
- [Procedures for mail flow rules in Exchange Server](https://learn.microsoft.com/en-us/exchange/policy-and-compliance/mail-flow-rules/mail-flow-rule-procedures)
