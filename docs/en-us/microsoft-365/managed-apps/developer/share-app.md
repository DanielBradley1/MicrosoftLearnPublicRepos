<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/share-app?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Share a Microsoft Copilot Managed Runtime app with users and groups \(preview\)

\[This article is prerelease documentation and is subject to change.\]

A Copilot Managed Runtime app is private to its owners until you share it. You can share an app in two fully revocable ways: directly with specific users or groups, or through a *People in your organization* share link that any member of your organization can redeem. You manage both sharing methods from the `ms` CLI.

Run the sharing commands from the directory that contains your app. Each command acts on that app automatically.

When a user has access, they can find and launch the app from the app portal at [https://managedapps.cloud.microsoft/](https://managedapps.cloud.microsoft/). For the end-user experience, see [What are Copilot Managed Runtime apps \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide).

## Access levels

When you share an app, choose one of two access levels:

| Access | What it grants |
| --- | --- |
| **Play** \(default\) | Run the app. This access level is right for end users. |
| **Edit** | Modify the app's source. This access level is for collaborators who develop the app with you. |

The two levels are independent, and granting or revoking one doesn't affect the other.

## Grant access to users or groups

Use [`ms app share`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share) with a comma-separated list of email addresses or Microsoft Entra object IDs:

```bash
ms app share <principals> [--access play | edit]
```

For example, to let two coworkers run the app:

```bash
ms app share alok@contoso.com,maria@contoso.com
```

To grant edit access to a collaborator:

```bash
ms app share dev-team@contoso.com --access edit
```

The CLI automatically looks up email addresses. It reports any entry it can't resolve as a warning, and the command proceeds with the entries that it does resolve. If none resolve, the command fails.

## Revoke access

Use [`ms app unshare`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-unshare) to remove access:

```bash
ms app unshare <principals> [--access play | edit]
```

`unshare` only changes the access level you specify. For example, revoking `edit` leaves a user's `play` access intact:

```bash
ms app unshare dev-team@contoso.com --access edit
```

Removing a principal who has no access at the requested level is a no-op, and it doesn't fail.

## Share an app with a link

A share link is a *People in your organization* link you can hand out instead of adding recipients one by one. Like a *People in your organization* link in SharePoint and OneDrive, it's a transferable, revocable key that only members of your organization can use. The first time a member opens the link, they sign in if they aren't already, and they're granted access to run the app. Guests and other people outside your organization can't use the link. Share links are revocable, so you can cut off access later without tracking down individual users.

### Create a link

Use [`ms app share link create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share-link-create) to generate a *People in your organization* share link for the current app:

```bash
ms app share link create
```

The command returns a short link ID, the share URL, and the access it grants. Distribute the URL to your recipients.

### List existing links

Use [`ms app share link list`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share-link-list) to view all active share links for the current app:

```bash
ms app share link list
```

### Revoke a link

Use [`ms app share link revoke`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share-link-revoke) to remove the access of everyone who redeemed a link, and then delete the link:

```bash
ms app share link revoke --link-id <id>
```

- `--link-id <id>`: The link ID returned when you created the link. Required.
- `--force`: Skips the confirmation prompt.

Tip

Use direct sharing for a known set of users, and a share link when you want to broadcast an app, for example by posting it to a team channel, while retaining the ability to revoke access for everyone at once.
