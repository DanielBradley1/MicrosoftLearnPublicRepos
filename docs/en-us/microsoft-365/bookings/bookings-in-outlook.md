<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/bookings/bookings-in-outlook?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Turn off Personal Bookings

Personal Bookings and Bookings share the same licensing model. However, Bookings doesn't have to be turned on for the organization using tenant settings for users to access Personal Bookings. The Bookings app must be enabled for users to have access to Personal Bookings.

To turn on Personal Bookings without access to Bookings, block access to Microsoft Bookings using the [OWA Mailbox policy PowerShell command](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-owamailboxpolicy) or follow the instructions here: [Turn Microsoft Bookings on or off](https://learn.microsoft.com/en-us/microsoft-365/bookings/turn-bookings-on-or-off?view=o365-worldwide).

## Turn Personal Bookings on or off

Personal Bookings can be turned on or off for your entire organization or specific users. When Personal Bookings is turned on, users can create a Personal Bookings page and share links with others inside or outside your organization.

Note

Tenant admins won't be able to control Personal Bookings access via EWS organization configuration \(Set-OrganizationConfig\) or per-user CAS Mailbox settings \(Set-CASMailbox\) anymore. Instead, they will need to use the OWA Mailbox Policy \(Set-OwaMailboxPolicy\) to control Personal bookings access within the organization.

Organization level: To identify if personal bookings is enabled/ disabled for your organization, admins can run the following PowerShell command:

```PowerShell
Get-OrganizationConfig | Select-Object EwsEnabled, EwsApplicationAccessPolicy, EwsBlockList, EwsAllowList
```

Only these two configuration responses ensure that the BWM is ENABLED for an Organization:

![Screenshot of check bwm 1.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/check-bwm-1.png?view=o365-worldwide)

![Screenshot of check bwm 2.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/check-bwm-2.png?view=o365-worldwide)

Note: All other configuration responses indicate that BWM is DISABLED for the organization.

Per user settings:

```PowerShell
Get-CASMailbox -Identity <smtp> | Select EwsEnabled, EwsApplicationAccessPolicy,  EwsBlockList, EwsAllowList
```

Only these two configuration responses ensure that the BWM is ENABLED for a user:

![Screenshot of check user 1.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/check-user-1.png?view=o365-worldwide)

![Screenshot of Check user 2.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/check-user-2.png?view=o365-worldwide)

Note: All other configuration responses indicate that BWM is DISABLED for the user.

1. To DISABLE Personal Bookings for your entire organization:

   Admin should run following PowerShell commands:

   ```PowerShell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -PersonalBookingsDisabled $true
   ```


   Verification:


   ```PowerShell
   Get-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" | Select PersonalBookingsDisabled
   ```


   Expected Output:


   ![Screenshot of disable output org.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/disable-output.png?view=o365-worldwide)


   Result:


   ![Screenshot of disable org result.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/disable-org-result.png?view=o365-worldwide)

2. To ENABLE Personal Bookings only for specific users \(all others blocked\):

   a. First, disable org-wide: Perform above steps.

   b. Next, enable for specific users by assigning a separate policy: Creating a new custom policy:

   ```PowerShell
   New-OwaMailboxPolicy -Name "BwmEnablePolicy"
   ```


   Output:


   ![Screenshot of enable output specific users.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/enable-output.png?view=o365-worldwide)


   Set User to this policy:


   ```PowerShell
   Set-CASMailbox -Identity <smtp> -OwaMailboxPolicy "BwmEnablePolicy"
   ```


   Verification:


   ```PowerShell
   Get-OwaMailboxPolicy -Identity "BwmEnablePolicy" | Select PersonalBookingsDisabled
   ```


   Output:


   ![Screenshot of set user to policy.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/set-user-policy.png?view=o365-worldwide)


   Result:


   ![Screenshot of result user policy.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/result-user.png?view=o365-worldwide)

3. To DISABLE Personal Bookings only for specific users \(all others are enabled\):

   a. First, enable org-wide: It is a default feature, or admin can reset by using command:

   ```PowerShell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -PersonalBookingsDisabled $false
   ```


   b. Next, Disable for specific users by assigning a separate policy: Creating a new custom policy:


   ```PowerShell
   New-OwaMailboxPolicy -Name "BwmDisablePolicy"
   ```


   Set PersonalBookingsDisabled true for this policy:


   ```PowerShell
   Set-OwaMailboxPolicy -Identity "BwmDisablePolicy" -PersonalBookingsDisabled $true
   ```


   Verification:


   ```PowerShell
   Get-OwaMailboxPolicy -Identity "BwmDisablePolicy" | Select PersonalBookingsDisabled
   ```


   Output:


   ![Screenshot of disable specific users output.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/disable-specific.png?view=o365-worldwide)


   Set User to this policy:


   ```PowerShell
   Set-CASMailbox -Identity <smtp> -OwaMailboxPolicy "BwmDisablePolicy"
   ```


   Verification:


   ![Screenshot of disable verification.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/disable-verification.png?view=o365-worldwide)


   Results:


   ![Screenshot of disable results.](https://learn.microsoft.com/en-us/microsoft-365/bookings/media/bookings-in-outlook/disable-results.png?view=o365-worldwide)
