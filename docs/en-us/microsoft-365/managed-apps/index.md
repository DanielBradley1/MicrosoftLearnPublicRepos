<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# What is Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

Copilot Managed Runtime hosts Microsoft 365 line-of-business applications that automatically inherit organizational governance, security, and compliance controls from the moment they're created. Whether you build an app through Copilot Cowork, Microsoft Copilot Studio, or the Copilot Managed Runtime SDK, the resulting app runs in a Microsoft-hosted environment, uses Microsoft Entra authentication, follows tenant governance policies, and is visible to admins in the Microsoft 365 admin center for monitoring and management.

Copilot Managed Runtime provides a unified experience for makers, developers, admins, and users. Organizations can accelerate app creation while maintaining centralized oversight, security, lifecycle management, and compliance controls.

This article explains the entry points where you can **create** apps, the unified location where you can **find and run** apps already available to you, and further resources for Copilot Managed Runtime users, makers, developers, and administrators.

## Three ways to create an app

| Entry point | Who it's for | How it works |
| --- | --- | --- |
| **Build apps in Cowork** | Business users who want to describe an app in a chat and keep working | From a Cowork session, ask for an app \(or use the **App builder** skill\). Cowork builds the app, lets you preview it, and helps you publish and share it. Requires enrollment in the [Frontier program](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#build-apps-with-the-app-skill-frontier). |
| **Create apps in Microsoft Copilot Studio** | Makers who want more control over the build, preview, and publish steps | Sign in to Copilot Studio, turn on the **Preview** experience, and select **Apps** in the navigation. Describe the app in natural language or start from existing data; Copilot Studio proposes a plan, generates a draft, and lets you refine it in an interactive preview before you publish and share. More information: [Create an app in Microsoft Copilot Studio \(preview\)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/create-app). |
| **Develop with the Copilot Managed Runtime SDK and CLI** | Professional developers who want a code-first workflow | Install the `ms` CLI \(`@microsoft/managed-apps-cli`\) and the `@microsoft/managed-apps` SDK to scaffold, build, and deploy an app from the command line, manually or with the coding agent plugin. More information: [Copilot Managed Runtime SDK overview \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide). |

All three paths produce the same kind of artifact: an app that runs in Copilot Managed Runtime, inherits your tenant's default governance policy \(approved connectors, sharing rules, content security policy\), and shows up in the admin inventory described below.

## One place to find and run your apps

Regardless of how an app was created, people go to one place to see the apps they have access to and open them: the **Copilot Managed Runtime portal** at [`https://managedapps.cloud.microsoft`](https://managedapps.cloud.microsoft/). This portal is the day-to-day landing page for app users, separate from the developer tools used to build an app and separate from the admin center used to govern it.

## How the pieces fit together

The following table summarizes the roles and Microsoft surfaces involved in creating, developing, using, and governing apps in Copilot Managed Runtime.

| Role | Where they work | What they do |
| --- | --- | --- |
| **User** | [managedapps.cloud.microsoft](https://managedapps.cloud.microsoft/) | Finds and opens the apps they can access. |
| **[Maker/business user](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#build-apps-with-app-builder-frontier)** | Copilot Cowork | Describes an app in chat and lets Cowork's app builder create it. |
| **[Maker](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/apps-overview)** | Microsoft Copilot Studio | Uses the **Create apps** tile to build an app from natural language or existing data, then previews, publishes, and shares it. |
| [**Professional developer**](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide) | CLI/SDK \(`ms` CLI, `@microsoft/managed-apps`\) | Scaffolds, codes, and deploys an app, optionally with an AI coding agent. |
| **[Admin](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide)** | Microsoft 365 admin center \(**Apps > All apps**\) | Sees every app built with Copilot Managed Runtime across the tenant, reviews governance defaults, monitors health, and manages security and compliance - no matter which surface built the app. |

For the full picture of concepts, governance, and administration, start with [Copilot Managed Runtime overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide), which provides further technical details for admins and developers.

## Related information

- [Copilot Managed Runtime overview and key concepts for admins \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide)
- [Copilot Managed Runtime SDK overview \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide)
- [Build apps with app builder \(Frontier\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#build-apps-with-app-builder-frontier)
- [Create an app in Microsoft Copilot Studio \(preview\)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/create-app)
