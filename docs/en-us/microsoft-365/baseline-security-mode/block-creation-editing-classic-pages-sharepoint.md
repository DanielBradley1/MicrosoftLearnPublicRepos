<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-creation-editing-classic-pages-sharepoint?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block creation and editing of classic SharePoint pages

Classic SharePoint pages, including user created publishing pages, wiki pages, web part pages, and other classic page types, are legacy experiences that depend on older frameworks. These user created pages may contain security vulnerabilities that can introduce security risks through harmful script injection and unsupported customizations.

This setting blocks users from creating or editing classic pages in publishing, wiki and web part types, and restricting collateral infrastructure, helping organizations strengthen security and move toward modern SharePoint experiences.

You must be a member of the [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) role to be able to configure this setting.

## Why this setting matters

Classic pages and publishing features are legacy capabilities that are no longer recommended for new use. They present ongoing security issues, maintenance challenges, and inconsistent governance. Blocking creation and editing helps reduce vulnerabilities and encourages use of modern SharePoint pages or the SharePoint Framework \(SPFx\) for secure, supportable customization.

## How this setting works

When enabled:

- **New classic pages can't be created** Classic page templates are removed from the New menu, preventing creation of publishing, wiki, and web part pages.
- **Unpublished classic pages can't be saved as drafts** Pages already created but not published can't enter or stay in a draft state.
- **Draft classic pages can't be published** Checked in or draft classic pages can no longer be published.
- **Published classic pages can't be edited** Existing pages remain viewable but can't be modified. This setting also supports restricting classic publishing sites and related legacy features:

  - Classic publishing sites can't be created at site collection and subsite levels.
  - Classic publishing feature can't be enabled at site collection and subsite levels.

Reporting is supported to provide historical usage on classic pages. The **downloadable CSV report** shows which classic pages have recent changes and the SharePoint sites where they reside, helping you identify potential security risks.
