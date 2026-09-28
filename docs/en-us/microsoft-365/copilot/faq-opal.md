<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/faq-opal -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions about Opal \(Frontier\) in Microsoft Copilot

Opal is an enterprise AI-powered capability under the Frontier program in Microsoft Copilot.

## Why does my user see the message 'You don't have access'?

Verify if the user is part of the correct security group included in the Microsoft 365 admin center setting. The owner of the security group must also be in the security group.

## Why does my user see the message 'Opal is under construction'?

Verify that you have gone through setup on the Opal admin portal. This message most frequently appears when the organization admin has not set up a Cloud PC pool.

## Why is Opal saying a website is blocked in the Cloud PC?

- Verify if the website is included in this section **Opal Admin Portal** -> **Cloud PC Setup** -> **Manage Access**. - Format the URL pattern using [this reference](https://go.microsoft.com/fwlink/?linkid=2095322). - Verify that the URL is correct; some authentication URLs follow different patterns than expected.

## Why can't users connect to the Cloud PC?

Make sure your users turn on pop-ups using the browser settings. Sometimes, an authentication window pops up and is required before the Cloud PC can connect.

## Why do my users see a black screen when they open a Cloud PC?

Your organization might have Windows Autopilot, or Enrollment Status Page, turned on for all devices. There's a known issue where this feature blocks Opal devices. Follow the steps described here to create a filter for Opal Cloud PCs and disable Windows Autopilot for those devices. [Create a filter for your Cloud PCs](https://learn.microsoft.com/en-us/windows-365/enterprise/create-filter)
