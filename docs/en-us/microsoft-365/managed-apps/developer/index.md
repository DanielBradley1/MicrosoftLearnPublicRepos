<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Microsoft Copilot Managed Runtime SDK overview \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

The Copilot Managed Runtime SDK accelerates the development of internal line-of-business apps that automatically comply with IT governance policies. Apps built with the SDK are hosted with Copilot Managed Runtime, include built-in Microsoft Entra authentication without requiring custom code, and can securely connect to more than 1,500 data sources such as Microsoft Graph, SQL, and SharePoint.

The SDK supports developers using their preferred tools, including Visual Studio Code, and underpins both Microsoft and third-party app creation experiences that publish Copilot Managed Runtime apps.

You can fully view and govern apps in the Microsoft 365 admin center, where they appear in centralized inventory experiences. They include out-of-the-box usage analytics to track adoption and built-in operational health metrics with alerting to detect and resolve issues. Governance policies, such as data source restrictions, are enforced automatically, ensuring apps comply with organizational standards from day one.

Learn how developers build apps from a command line.

**Key features include:**

- Microsoft Entra authentication and authorization out of the box
- Access to more than 1,500 connectors, callable directly from JavaScript and TypeScript
- A native Git inner loop with either a platform-managed repository or your own external GitHub repository
- Adherence by default to your organization's IT policies, including sharing limits, Conditional Access, Advanced Connector Policies, and Data Loss Prevention
- A GitHub Copilot plugin so you can get the most from your coding agent that helps you build and edit your business apps

## Prerequisites

Apps require a few developer tools available on the command line and appropriate end-user licensing.

### Install the following developer tools

Use these tools to build apps locally:

- Your IDE of choice. For example, [Visual Studio Code](https://code.visualstudio.com/).
- [Node.js](https://nodejs.org/) \(LTS version\) >= v24.11.0.
- [Git](https://git-scm.com/) >= v2.27.0.
- [Git Credential Manager](https://github.com/git-ecosystem/git-credential-manager). If you install Git on Windows, you might already have GCM installed and can skip this step. Run `git credential-manager --version` to verify.
- The Microsoft Copilot Managed Runtime CLI. Install it globally with `npm install -g @microsoft/managed-apps-cli` and verify with `ms --version`.
- If using a remote GitHub repository \(optional\), use a repository owned by an organization on GitHub Enterprise Cloud and install [Microsoft Managed Apps](https://github.com/marketplace/microsoft-managed-apps) in the organization and repositories you'll use.

### License end users

Licensing is enforced when developers run an app locally by using the Copilot Managed Runtime CLI and when end users run apps. Other CLI development activities don't enforce licensing.

#### Licensing options

Users must have one of the following to run an app:

- **Power Apps Premium plan:** Covers all app operations without consuming Copilot Credits.
- **Managed Application Copilot Credits:** Credits are charged each time an app launches and for each API call. Each API call consumes 0.1 credits. Learn more at [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

These requirements apply both to developers running apps locally and to end users running apps.

#### Insufficient credits

Users who rely on Copilot Credits and don't meet the credit requirements to run an app initially receive a warning and can continue to use the app without charge. Access is then blocked when either of the following limits is reached, whichever occurs first:

- The user completes **20 app operations**.
- The user uses the app for **five minutes**.

Users covered by a Power Apps Premium plan aren't subject to these credit requirements.

## Developer tools

Developers use the following tools when creating apps:

| Tool | Description |
| --- | --- |
| The Copilot Managed Runtime CLI \(`@microsoft/managed-apps-cli`\) | A single command-line tool, invoked as `ms`, for creating, developing, and deploying apps. |
| The Copilot Managed Runtime SDK \(`@microsoft/managed-apps`\) | A client library for calling connectors and interacting with the platform at runtime. |
| Native Git | The CLI doesn't replace Git. You use `git add`, `git commit`, and `git push` the same way you would on any other project. Builds and deploys flow from real commits in a real repository. |

You can edit code in any IDE. There's no required editor and no required template beyond the scaffold the CLI produces.

## Repository options

Every app has a repository associated with it. You choose the repository type when you create the app, and you can't change the choice later.

| Option | Description |
| --- | --- |
| Platform-managed Git \(default\) | The platform provisions a managed Git repository when you create an app - no extra setup required. |
| Bring your own GitHub repository | Bind an app to one of your repos at create or init time by passing `--repo <url>`. The platform builds, scans, and deploys from your repository, and your existing branch policies and pull request reviews continue to apply. |

Note

The repository must be owned by an organization on GitHub Enterprise Cloud. Repositories can use a `github.com` host or a `*.ghe.com` data-residency host. GitHub Enterprise Server, repositories owned by personal accounts, organizations that aren't on GitHub Enterprise Cloud, and other providers such as Azure DevOps aren't supported. Repository URLs must use a full `https://` scheme.

Configure repository visibility and other repository management policies in GitHub Enterprise Cloud. For more information, see [Enforcing repository management policies in your enterprise](https://docs.github.com/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#about-policies-for-repository-management-in-your-enterprise).

## Copilot Managed Runtime availability

All eligible tenants in commercial cloud automatically get Copilot Managed Runtime. Tenant administrators don't need to take any action to turn on the feature, and there's no separate installation step.

## Explore the repo and report issues

To help you get started and stay productive, use the resources available in the [Copilot Managed Runtime CLI GitHub repository](https://github.com/microsoft/Managed-Apps).

### Submit new issues

To share feedback or seek guidance, [open a new issue in the repository](https://github.com/microsoft/managed-apps/issues).

Tip

If you find an existing issue or enhancement that applies to you, upvote or comment on it to signal its priority to the product team.

### Review completed issues

Check the **Closed** tab in **Issues** to see how other customers solved problems or requested enhancements. Closed issues are a great way to learn from real-world scenarios and confirm whether a fix or feature you need is already available.

## Next steps

[Quickstart: Build a Microsoft Copilot Managed Runtime app with GitHub Copilot \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-github-copilot?view=o365-worldwide)

[Quickstart: Create an app with the Copilot Managed Runtime SDK \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-managed-apps-cli?view=o365-worldwide)
