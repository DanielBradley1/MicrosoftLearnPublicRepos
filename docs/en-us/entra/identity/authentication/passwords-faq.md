<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/passwords-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Self-service password reset frequently asked questions

The following are some frequently asked questions \(FAQ\) for all things related to self-service password reset.

If you have a general question about Microsoft Entra ID and self-service password reset \(SSPR\) that's not answered here, you can ask the community for assistance. You can do this on the [Microsoft Q&A question page for Microsoft Entra ID](https://learn.microsoft.com/en-us/answers/topics/azure-active-directory.html). Members of the community include engineers, product managers, MVPs, and fellow IT professionals.

This FAQ is split into the following sections:

- Questions about password reset registration
- Questions about password reset
- Questions about password change
- Questions about password management reports
- Questions about password writeback

## Password reset registration

### Can my users register their own password reset data?

> Yes. As long as password reset is enabled and they're licensed, users can go to the password reset registration portal \([https://aka.ms/ssprsetup](https://aka.ms/ssprsetup)\) to register their authentication information. Users can also register through the Access Panel \([https://myapps.microsoft.com](https://myapps.microsoft.com)\). To register through the Access Panel, they need to select their profile picture, select **Profile**, and then select the **Register for password reset** option.
> 
> If you enable [combined registration](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-registration-mfa-sspr-combined), users can register for both SSPR and Microsoft Entra multifactor authentication at the same time.

### If I enable password reset for a group and then decide to enable it for everyone are my users required re-register?

> No. Users who populated authentication data aren't required to re-register.

### Can I define password reset data on behalf of my users?

> Yes, you can do so with Microsoft Entra Connect, PowerShell, the [Microsoft Entra admin center](https://entra.microsoft.com), or the [Microsoft 365 admin center](https://admin.microsoft.com). For more information, see [Data used by Microsoft Entra self-service password reset](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-authenticationdata).

### Can I synchronize data for security questions from on-premises?

> No, this isn't possible today.

### Can my users register data in such a way that other users can't see this data?

> Yes. When users register data by using the password reset registration portal, the data is saved into private authentication fields that are visible only to [Privileged Authentication Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-authentication-administrator) and the user.

### Do my users have to be registered before they can use password reset?

> No. If you define enough authentication information on their behalf, users don't have to register. Password reset works as long as you properly format the data stored in the appropriate fields in the directory.

### Can I synchronize or set the authentication phone, authentication email, or alternate authentication phone fields on behalf of my users?

> The fields that are able to be set by a [Privileged Authentication Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-authentication-administrator) are defined in the article [SSPR Data requirements](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-authenticationdata).

### How does the registration portal determine which options to show my users?

> The password reset registration portal shows only the options that you enabled for your users. These options are found under the **User Password Reset Policy** section of your directory's **Configure** tab. For example, if you don't enable security questions, then users aren't able to register for that option.

### When is a user considered registered?

> A user is considered registered for SSPR when they registered at least the **Number of methods required to reset** a password that you set in the [Microsoft Entra admin center](https://entra.microsoft.com).

## Password reset

### Do you prevent users from multiple attempts to reset a password in a short period of time?

> Yes, there are security features built into password reset to protect it from misuse.
> 
> Users can attempt to validate their information \(such as their phone number\), but if they're unable to prove their identity five times within a 24-hour period, they're locked out for 24 hours.
> 
> Users can try to validate a phone number, auth app, send a text message, or validate security questions and answers only five times within an hour before they're locked out for 24 hours.
> 
> Users can send an email a maximum of 10 times within a 10-minute period before they're locked out for 24 hours.
> 
> The counters are reset once a user resets their password.

### How long should I wait to receive an email, text message, or phone call from password reset?

> Emails, text messages, and phone calls should arrive in under a minute. The normal case is 5 to 20 seconds. If you don't receive the notification in this time frame:
> 
> - Check your junk folder.
> - Check that the number or email being contacted is the one you expect.
> - Check that the authentication data in the directory is correctly formatted, for example, +1 4255551234 or *user@contoso.com*.

### What languages are supported by password reset?

> The password reset UI, text messages, and voice calls are localized in the same languages that are supported in Microsoft 365.

### What parts of the password reset experience get branded when I set the organizational branding items in my directory's configure tab?

> The password reset portal shows your organization's logo and allows you to configure the "Contact your administrator" link to point to a custom email or URL. Any email that's sent by password reset includes your organization's logo, colors, and name in the body of the email, and is customized from the settings for that particular name.

### How can I educate my users about where to go to reset their passwords?

> Try some of the suggestions in our [SSPR deployment](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-deployment) article.

### Can I use this page from a mobile device?

> Yes, this page works on mobile devices.

### Do you support unlocking local Active Directory accounts when users reset their passwords?

> Yes. When a user resets their password, if password writeback is deployed through Microsoft Entra Connect, that user's account is automatically unlocked when they reset their password.

### How can I integrate password reset directly into my user's desktop sign-in experience?

> If you're a Microsoft Entra ID P1 or P2 customer, you can install Microsoft Identity Manager at no additional cost and deploy the on-premises password reset solution.

### Can I set different security questions for different locales?

> No, this isn't possible today.

### How many questions can I configure for the security questions authentication option?

> You can configure up to 20 custom security questions in the [Microsoft Entra admin center](https://entra.microsoft.com).

### How long can security questions be?

> Security questions can be 3 to 200 characters long.

### How long can the answers to security questions be?

> Answers can be 3 to 40 characters long.

### Are duplicate answers to security questions rejected?

> Yes, we reject duplicate answers to security questions.

### Can a user register the same security question more than once?

> No. After a user registers a particular question, they can't register for that question a second time.

### Is it possible to set a minimum limit of security questions for registration and reset?

> Yes, one limit can be set for registration and another for reset. Three to five security questions can be required for registration, and three to five questions can be required for reset.

### I configured my policy to require users to use security questions for reset, but the Azure administrators seem to be configured differently.\*\*

> This is the expected behavior. Microsoft enforces a strong default two-gate password reset policy for any Azure administrator role. This prevents administrators from using security questions. You can find more information about this policy in the [Password policies and restrictions in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-policy) article.

### If a user has registered more than the maximum number of questions required to reset, how are the security questions selected during reset?

> *N* number of security questions are selected at random out of the total number of questions a user has registered for, where *N* is the amount that is set for the **Number of questions required to reset** option. For example, if a user has registered five security questions, but only three are required to reset a password, three of the five questions are randomly selected and are presented at reset. To prevent question hammering, if the user gets the answers to the questions wrong the selection process starts over.

### How long are the email and text message one-time passcodes valid?

> The session lifetime for password reset is 15 minutes. From the start of the password reset operation, the user has 15 minutes to reset their password. The one-time passcodes are valid for 5 minutes during the password reset session.

### Can I block users from resetting their password?

> Yes, if you use a group to enable SSPR, you can remove an individual user from the group that allows users to reset their password. If the user is a [Privileged Authentication Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-authentication-administrator), they can reset their password and this can't be disabled.

## Password change

### Where should my users go to change their passwords?

> Users can change their passwords anywhere they see their profile picture or icon, like in the upper-right corner of their [Office 365](https://portal.office.com) portal or [Access Panel](https://myapps.microsoft.com) experiences. Users can change their passwords from the [Access Panel Profile page](https://account.activedirectory.windowsazure.com/r#/profile). Users can also be asked to change their passwords automatically at the Microsoft Entra sign-in page if their passwords are expired. Finally, users can browse to the [Microsoft Entra password change portal](https://account.activedirectory.windowsazure.com/ChangePassword.aspx) directly if they want to change their passwords.

### Can my users be notified in the Office portal when their on-premises password expires?

> Yes, this is possible today if you use Active Directory Federation Services \(AD FS\). If you use AD FS, follow the instructions in the [Sending password policy claims with AD FS](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-to-send-password-expiry-claims?f=255&MSPPError=-2147217396) article. If you use password hash synchronization, this isn't possible today. We don't sync password policies from on-premises directories, so it's not possible for us to post expiration notifications to cloud experiences. In either case, it's also possible to [notify users whose passwords are about to expire through PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/23313.notify-active-directory-users-about-password-expiry-using-powershell.aspx).

### Can I block users from changing their password?

> For cloud-only users, password changes can't be blocked. For on-premises users, you can set the **User can't change password** option to selected. The selected users can't change their password.

## Password management reports

### How long does it take for data to show up on the password management reports?

> Data should appear on the password management reports in 5 to 10 minutes. In some instances, it might take up to an hour to appear.

### How can I filter the password management reports?

> To filter the password management reports, select the small magnifying glass to the extreme right of the column labels, near the top of the report. For more comprehensive filtering, you can download the report to Excel and create a pivot table.

### What is the maximum number of events that are stored in the password management reports?

> Up to 75,000 password reset or password reset registration events are stored in the password management reports, spanning back as far as 30 days. We're working to expand this number to include more events.

### How far back do the password management reports go?

> The password management reports show operations that occurred within the last 30 days. For now, if you need to archive this data, you can download the reports periodically and save them in a separate location.

### Is there a maximum number of rows that can appear on the password management reports?

> Yes. A maximum of 75,000 rows can appear on either of the password management reports, whether they're shown in the UI or are downloaded.

### Is there an API to access the password reset or registration reporting data?

> Yes, you can get this info from the [Authentication Methods Activity report](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity) or the [API to get password reset activity](https://learn.microsoft.com/en-us/graph/api/reportroot-list-usercredentialusagedetails). You can also use the [audit logs API](https://learn.microsoft.com/en-us/graph/api/resources/azure-ad-auditlog-overview) and filter by SSPR events.

## Password writeback

### How does password writeback work behind the scenes?

> See the article [How password writeback works](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-sspr-writeback) for an explanation of what happens when you enable password writeback and how data flows through the system back into your on-premises environment.

### How long does password writeback take to work? Is there a synchronization delay like there is with password hash sync?

> Password writeback is instant. It's a synchronous pipeline that works differently than password hash synchronization. Password writeback allows users to get real-time feedback about the success of their password reset or change operation. The average time for a successful writeback of a password is under 500 ms.

### If my on-premises account is disabled, how is my cloud account and access affected?

> If your on-premises ID is disabled, your cloud ID and access will also be disabled at the next sync interval through Microsoft Entra Connect. By default, this sync is every 30 minutes.

### If my on-premises account is constrained by an on-premises Active Directory password policy, does SSPR obey this policy when I change my password?

> Yes, SSPR relies on and abides by the on-premises Active Directory password policy. This policy includes the typical Active Directory domain password policy, and any defined, fine-grained password policies that are targeted to a user.

### What types of accounts does password writeback work for?

> Password writeback works for user accounts that are synchronized from on-premises Active Directory to Microsoft Entra ID, including federated, password hash synchronized, and Pass-Through Authentication Users.

### Does password writeback enforce my domain's password policies?

> Yes. Password writeback enforces password age, history, complexity, filters, and any other restriction you might put in place on passwords in your local domain.

### Is password writeback secure? How can I be sure I won't get hacked?

> Yes, password writeback is secure. To read more about the multiple layers of security implemented by the password writeback service, check out the [Password writeback security](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-writeback#password-writeback-security) section in the [Password writeback overview](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-sspr-writeback) article.

## Next steps

- [How do I complete a successful rollout of SSPR?](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-deployment)
- [Reset or change your password](https://support.microsoft.com/account-billing/reset-your-work-or-school-password-using-security-info-23dde81f-08bb-4776-ba72-e6b72b9dda9e)
- [Register for self-service password reset](https://support.microsoft.com/account-billing/register-the-password-reset-verification-method-for-a-work-or-school-account-47a55d4a-05b0-4f67-9a63-f39a43dbe20a)
- [Do you have a licensing question?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-licensing)
- [What data is used by SSPR and what data should you populate for your users?](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-authenticationdata)
- [What authentication methods are available to users?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks#authentication-methods)
- [What are the policy options with SSPR?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-policy)
- [What is password writeback and why do I care about it?](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-sspr-writeback)
- [How do I report on activity in SSPR?](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-reporting)
- [What are all of the options in SSPR and what do they mean?](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks)
- [I think something is broken. How do I troubleshoot SSPR?](https://learn.microsoft.com/en-us/entra/identity/authentication/troubleshoot-sspr)
