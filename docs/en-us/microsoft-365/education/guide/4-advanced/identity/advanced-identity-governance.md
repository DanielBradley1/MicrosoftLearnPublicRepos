<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-governance -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 2: Identity governance

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides an overview of advanced identity governance capabilities available to educational institutions with Microsoft 365 A5. It covers essential concepts and tools—including access reviews and entitlement management to help IT and security teams manage user access, maintain compliance, and protect sensitive data in dynamic academic environments.

## Requirements

- Microsoft 365 A5 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin
- Security Admin
- Compliance Admin

## Basic access certifications and reviews

Basic access certifications and reviews in education refer to the structured process of periodically validating who has access to what resources—such as applications, groups, and data—within an educational institution’s IT environment. This process is essential for maintaining security, ensuring compliance, and minimizing unnecessary or risky access, especially in dynamic environments like schools and universities.

**What are access certifications and reviews?**

In Microsoft Entra ID Governance, access reviews allow institutions to:

- Review and certify user access to apps, groups, and roles.
- Ensure only the right people retain access to sensitive or privileged resources.
- Automate revocation of access when it’s no longer needed.

These reviews can be configured to run on a schedule \(for example, quarterly\) and can be targeted at internal users, guest users, or privileged roles. They're useful in education where students, faculty, and staff frequently change roles, graduate, or leave the institution.

**Key capabilities for education:**

| Feature | Description |
| --- | --- |
| Multi-stage reviews | Up to three stages of review can be configured, allowing department heads, IT admins, and compliance officers to sequentially validate access. |
| Auto-remediation | Access is automatically revoked for users who are denied access or fail to respond. |
| Role and group targeting | Reviews can be scoped to Microsoft 365 groups, Teams, apps, or privileged roles. |
| Self-attestation | Users can be asked to justify their continued access, which is especially useful for guest users or temporary staff. |

**Benefits for educational institutions:**

- Compliance: Helps meet FERPA, GDPR, and internal audit requirements.
- Security: Reduces risk by removing stale or excessive access.
- Efficiency: Automates what would otherwise be a manual, error-prone process.
- Transparency: Provides audit trails and reporting for governance teams

## Basic entitlement management

Basic entitlement management refers to the foundational processes and tools used to govern and automate access to digital resources—such as applications, Microsoft Teams, SharePoint sites, and security groups—across students, faculty, staff, and external collaborators. This is primarily delivered through Microsoft Entra ID entitlement management, which is included in Microsoft 365 A5 or available as an add-on to A3.

**What is entitlement management?**

Entitlement management enables institutions to:

- Bundle resources into access packages \(for example, a package for "Math Faculty" might include access to Teams, grading systems, and SharePoint sites\).
- Automate access requests through a self-service portal \(My Access\).
- Define approval workflows for access \(for example, department head or IT admin approval\).
- Set expiration policies to automatically remove access when it’s no longer needed.
- Review and certify access periodically to ensure compliance.

This is useful in education organizations where users frequently change roles \(for example, students graduating, faculty onboarding\) and where external collaborators \(for example, guest lecturers, researchers\) need temporary access.

**Education-specific use cases:**

- Course-based access: Automatically grant students access to Teams, OneNote, and apps based on course enrollment.
- Faculty onboarding: Provision access to HR systems, curriculum tools, and department resources based on role.
- Guest access: Securely onboard external researchers or guest lecturers with time-limited access.
- Policy enforcement: Apply compliance policies \(for example, GDPR, FERPA\) to entitlements using tools like BYOE \(Bring Your Own Entitlement\) and privacy manager integrations.

**Key features:**

| Feature | Description |
| --- | --- |
| Access packages | Group apps, groups, and sites into reusable bundles. |
| Connected organizations | Manage access for external users from partner institutions. |
| Approval workflows | Multi-stage approvals for sensitive access requests. |
| Access reviews | Periodic re-certification of access to ensure least-privilege. |
| Expiration policies | Automatically remove access after a set period. |

**Integration with Microsoft 365 Education:**

- Microsoft Teams for class and staff collaboration
- SharePoint and OneDrive for secure content sharing
- Microsoft Intune for device compliance
- School Data Sync \(SDS\) for automated roster-based provisioning

## Entitlement management – separation of duties

Entitlement management with separation of duties \(SoD\) in education is a governance strategy that ensures users—such as students, faculty, staff, and external collaborators—receive only the access they need, and no more, to perform their roles. This approach helps educational institutions enforce least privilege, reduce insider risk, and meet compliance requirements like FERPA, GDPR, and SOX.

**What Is separation of duties in entitlement management?**

Separation of duties \(SoD\) is a security principle that prevents any single individual from having excessive control over critical systems or data. In the context of Microsoft Entra ID entitlement management, SoD is enforced by:

- Defining access packages with clear boundaries.
- Requiring multi-stage approvals for sensitive access.
- Using role-based delegation to distribute responsibility across catalog creators, owners, and access package managers.
- Auditing access history to ensure no user accumulates conflicting roles over time.

SoD is important in education where users often hold multiple roles \(for example, a faculty member who is also a department chair\) and where external collaborators may need temporary access.

**Education-specific use cases:**

- Student information systems \(SIS\): Prevent a single user from both entering and approving grades or financial aid decisions.
- Research environments: Ensure that no one person can both provision and approve access to sensitive datasets.
- IT admin roles: Separate duties between those who manage access packages and those who approve them, reducing the risk of privilege abuse.

**Key capabilities in Microsoft Entra:**

| Feature | Description |
| --- | --- |
| Access packages | Bundle apps, groups, and sites into manageable units with defined approval workflows. |
| Delegated roles | Catalog Creators, Catalog Owners, and Access Package Managers each have scoped responsibilities. |
| Audit trails | Track who requested, approved, and used access—critical for compliance and investigations. |
| Time-bound access | Automatically expire access to prevent privilege creep. |

## Privileged identity management \(PIM\)

Privileged Identity Management \(PIM\) in education is a Microsoft Entra ID feature that enables institutions to manage, control, and monitor privileged access to critical resources—such as Microsoft 365, Azure, Intune, and other Microsoft Online Services—through just-in-time, approval-based, and time-bound role activation. This helps reduce the risk of excessive, unnecessary, or misused access, which is especially important in educational environments where users often hold multiple roles or transition frequently.

**What PIM does in education:**

- Minimize standing privileges by assigning roles as "eligible" rather than "active."
- Enforce just-in-time access so users activate roles only when needed.
- Require approval and justification for role activation, increasing accountability.
- Enforce MFA before activating privileged roles.
- Audit and review access through built-in reporting and access reviews.

PIM is useful in education settings where IT staff, faculty, and student workers may need temporary elevated access to systems like SIS, LMS, or administrative portals.

**Education-specific use cases:**

- IT admins: Grant temporary access to Azure or Intune for device management or policy updates.
- Faculty researchers: Provide time-limited access to secure research environments or datasets.
- Student workers: Allow access to administrative tools only during scheduled shifts or projects.
- External collaborators: Enable secure, auditable access for guest lecturers or partner institutions.

**Key features:**

| Feature | Description |
| --- | --- |
| Time-bound access | Roles are activated only for a defined period. |
| Approval workflows | Role activation can require approval from designated reviewers. |
| MFA enforcement | Ensures strong authentication before granting elevated access. |
| Access reviews | Periodic checks to confirm users still need their roles. |
| Audit logs | Full visibility into who activated what, when, and why. |

**Licensing requirements:**

- PIM requires a Microsoft Entra ID Plan 2 license, which is included in Microsoft 365 A5—commonly used in education.
- It can also be added to A3 environments as an upgrade.
