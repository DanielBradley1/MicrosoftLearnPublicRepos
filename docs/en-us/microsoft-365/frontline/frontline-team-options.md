<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/frontline/frontline-team-options?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-12-17 -->

# How to find the best frontline team solution for your organization

## Overview

Frontline teams are a collection of people, content, and tools within an organization for different frontline worker locations. When deploying your frontline teams, you have different options for how you can manage team membership. You can choose between flexible team membership, static team membership, or a combination of both.

### Key considerations

- You can choose a mix of flexible membership teams and static frontline teams for your organization.
- You can convert static frontline teams to flexible membership teams in the Microsoft Entra admin center by using the [link your existing frontline teams feature](https://learn.microsoft.com/en-us/microsoft-365/frontline/link-your-existing-frontline-teams-to-be-managed-with-flexible-membership).

## When should I choose flexible membership teams?

Flexible membership teams ensure your team membership is always up to date based on attributes you define in Microsoft Entra ID. As frontline employees onboard, offboard, or change locations, team membership reflects the updates from Microsoft Entra ID. However, because these teams are flexible local team owners can add or remove members as needed.

You should use flexible membership teams if:

- You want your workers' team membership to be managed automatically.
- You have Microsoft Entra attributes that can define who is a frontline worker and what locations they work in.
- You want to simplify the process of creating a team for each frontline location, including support for creating new teams when a new location opens.

[Learn more about deploying frontline teams with flexible membership from the Teams admin center](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-flexible-membership-teams-at-scale).

## When should I choose static teams?

Static teams let you choose which users to put in which team at the time of team creation. Team owners can manually add and remove members. Admins can also rerun the [Deploy static teams at scale PowerShell script](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-teams-at-scale?view=o365-worldwide) to keep membership up to date.

You should use static teams if:

- You want to manage team members and owners manually or delegate management to the team owners.
- You can't identify your frontline workforce with a Microsoft Entra attribute or you can't define your frontline locations with a Microsoft Entra attribute. [Learn more about deploying static frontline teams with PowerShell](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-teams-at-scale?view=o365-worldwide).

## Frontline team deployment best practices

When evaluating the right solution for your organization, we recommend you do the following:

1. Plan your frontline deployment.
2. Test the deploy tools—[flexible team creation in the Teams admin center](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-dynamic-teams-at-scale?view=o365-worldwide) or [static team creation using the PowerShell solution](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-teams-at-scale?view=o365-worldwide). Keep in mind that static teams aren't managed automatically.
3. Deploy to a pilot location.
4. Deploy to a broader set of locations using a phased approach.
