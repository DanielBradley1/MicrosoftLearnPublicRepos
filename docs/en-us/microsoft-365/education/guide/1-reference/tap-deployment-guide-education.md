<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/tap-deployment-guide-education -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# School-level Temporary Access Pass \(TAP\) deployment guide

## Overview and purpose

As Microsoft retires security questions for Self-Service Password Reset \(SSPR\) in March 2027, school districts need a modern, secure, and practical replacement for students who can't use mobile devices or alternative authentication methods.

This guide walks your district IT team through deploying Temporary Access Pass \(TAP\) using Microsoft Entra Administrative Units \(AUs\) to delegate TAP generation to school-level staff. Teachers and building administrators can issue recovery passes for their own students without involving central IT.

## Architecture overview

The solution follows a hierarchical delegation model:

| **Level** | **Role** | **Capability** |
| --- | --- | --- |
| District Tenant | Central IT \(Global Admin\) | Enable TAP policy, create AUs, assign scoped roles |
| Administrative Unit | School-Level IT / Office Staff | Manage students and staff within their school only |
| Authentication Admin \(Scoped\) | Teachers / Building Admins | Issue TAPs for students within their school AU only |
| Student Account | Student | Use TAP to recover access - no phone required |

Note

**🔐 Key Principle:** Teachers can only issue TAP for students within their own school's Administrative Unit. They can't affect students at other schools or access district-wide settings.

## Prerequisites

| **Requirement** | **Details** |
| --- | --- |
| License | Microsoft Entra ID P1 \(included in Microsoft 365 A3/A5 for Education\) |
| Central IT Role | Global Administrator or Privileged Role Administrator |
| Teacher Role \(scoped\) | Authentication Administrator scoped to the school's AU |
| Student Accounts | Microsoft Entra ID user accounts provisioned in the tenant |
| Admin Center Access | [https://entra.microsoft.com](https://entra.microsoft.com) |

## Phase 1 – Enable the TAP policy \(Central IT\)

**This is a one-time tenant-wide configuration performed by Central IT.**

### Step 1: Enable TAP in Authentication Methods

1. Sign in to [https://entra.microsoft.com](https://entra.microsoft.com) as Authentication Policy Administrator or higher.
2. Go to **Protection** > **Authentication methods** > **Policies**.
3. Select **Temporary Access Pass** from the list.
4. Toggle **Enable** to **On**.
5. Under **Target**, select **Include** → choose a student security group \(for example, All-Students\) or select **All users**.
6. Select **Configure** and apply the recommended education settings shown in the following table.
7. Select **Update**, and then **Save**.

| **Setting** | **Recommended Value \(K-12\)** | **Reason** |
| --- | --- | --- |
| Minimum Lifetime | One hour | Enough time for a student to sign in |
| Maximum Lifetime | Four hours | Limits exposure if TAP is lost or shared |
| Default Lifetime | Two hours | Balanced for a typical school day |
| One-Time Use | Yes | TAP invalidated after first use - prevents reuse |
| Length | Eight characters | Default; sufficient complexity for student accounts |

Important

Setting One-Time Use = Yes is recommended for student accounts. Once used, the TAP is immediately invalidated even if time remains on the pass.

## Phase 2 – Create Administrative Units per school \(Central IT\)

Administrative units \(AUs\) restrict a teacher's administrative permissions to only the students in their school - they can't accidentally affect accounts at other schools.

### Step 2: Create an administrative unit for each school

Repeat the following steps for each school in your district:

1. Sign in to [https://entra.microsoft.com](https://entra.microsoft.com) as Global Administrator or Privileged Role Administrator.
2. Go to **Identity → Overview → Administrative units**.
3. Select **+ Add**.
4. Name: AU - \[School Name\] \(for example, AU - Jefferson Elementary\).
5. Description: Students and staff for \[School Name\].
6. Set Membership type to **Assigned** \(or **Dynamic** - see tip\).
7. Select **Create**.

Tip

**Dynamic Membership:** For large districts, use Dynamic membership rules to autopopulate each AU. Example rule: user.department -eq "Jefferson Elementary". This automatically adds all users with that department attribute, eliminating manual maintenance as students enroll or transfer.

### Step 3: Add student accounts to each administrative unit

**Option A - Manual \(small schools\):**

1. Open the AU \(for example, AU - Jefferson Elementary\).
2. Select **Members → + Add members**.
3. Search for and select all student accounts for that school.
4. Select **Select** to save.

**Option B - Dynamic Rule \(recommended for large districts\):**

1. When creating the AU, set Membership type to Dynamic User.
2. Set the membership rule: user.department -eq "Jefferson Elementary"
3. Ensure student accounts have the Department attribute set in Microsoft Entra ID \(or synced from on-premises Active Directory\).

## Phase 3 – Assign Scoped Authentication Administrator role to teachers

This step gives teachers the ability to issue TAPs, but only for students in their own school's Administrative Unit.

### Step 4: Assign the Authentication Administrator Role Scoped to the School AU

1. Go to the administrative unit \(for example, AU - Jefferson Elementary\).
2. Select **Roles and administrators**.
3. Select **+ Add assignment**.
4. Search for and select the role: **Authentication Administrator**.
5. Under **Select members**, add the teachers or a Teacher Security Group for that school \(for example, Jefferson-Elementary-Staff\).
6. Select **Add**.

**What the scoped Authentication Administrator role allows:**

| **Permission** | **Granted?** |
| --- | :---: |
| ✅ Create TAPs for students in their AU | Yes |
| ✅ Reset authentication methods for students in their AU | Yes |
| ❌ Manage Global Admins or Privileged Authentication Admins | No |
| ❌ Access students in other school AUs | No |
| ❌ Change tenant-wide authentication policies | No |

## Phase 4 – Teacher TAP issuance workflow \(school-level staff\)

Once configured, this is the day-to-day process teachers follow when a student needs to recover access.

### Step 5: Teacher issues a TAP for a student

1. Teacher signs in to [https://entra.microsoft.com](https://entra.microsoft.com) with their school staff account.
2. Go to **Identity** > **Users**.
3. Search for the student's name or username.
4. Select the student account.
5. Select **Authentication methods** from the left-hand menu.
6. Select **+ Add authentication method**.
7. Choose **Temporary Access Pass** from the dropdown.
8. Configure: Activation = Immediate \| Lifetime = 2 hours \| One-time use = Yes.
9. Select **Add**.
10. ⚠️ Copy the TAP code immediately - it's only shown once and can't be retrieved later.
11. Provide the TAP code to the student verbally or on a printed slip.

Note

**Best Practice:** Never send TAP codes via email or Teams chat to the student. Always deliver the code in person or via a secure printed slip.

## Phase 5 – Student recovery process

### Step 6: Student uses the TAP to recover access

1. Student goes to [https://mysignins.microsoft.com](https://mysignins.microsoft.com) \(or opens any Microsoft 365 app\).
2. Enters their school username \(for example, jsmith@jeffersonelementary.edu\).
3. When prompted for authentication, selects **Use a Temporary Access Pass**.
4. Enters the TAP code provided by the teacher.
5. Student is now signed in and can reset their password or register new authentication methods \(for example, Windows Hello PIN\).
6. The TAP is invalidated immediately after first use \(if one-time use is enabled\).

## Phase 6 – PowerShell Automation \(optional\)

For districts managing hundreds of schools, TAP generation can be scripted to allow bulk issuance or integration with helpdesk ticketing systems.

```
# Connect to Microsoft Graph
Connect-MgGraph -Scopes "UserAuthenticationMethod.ReadWrite.All"

# Create a single-use TAP for a student (2-hour lifetime)
$properties = @{
    isUsableOnce      = $true
    lifetimeInMinutes = 120
    startDateTime     = (Get-Date).ToString("yyyy-MM-ddTHH:mm:ss")
}

$propertiesJSON = $properties | ConvertTo-Json

New-MgUserAuthenticationTemporaryAccessPassMethod `
    -UserId "jsmith@jeffersonelementary.edu" `
    -BodyParameter $propertiesJSON
```

Tip

Wrap this script in a simple web form or Power Automate flow for teachers who prefer not to navigate the Microsoft Entra admin portal directly.

## Security best practices

| **Practice** | **Recommendation** |
| --- | --- |
| TAP Lifetime | Keep to 2–4 hours maximum for student accounts |
| One-Time Use | Always enable for student recovery scenarios |
| TAP Delivery | Always deliver in person - never via email or chat |
| Audit Logs | Review TAP issuance logs in Microsoft Entra ID → Audit Logs monthly |
| Teacher Role Hygiene | Remove Authentication Administrator role from staff who leave the school |
| Dynamic AU Membership | Use dynamic rules to automatically remove transferred students from school AUs |
| Least Privilege | Don't assign Global Admin to teachers - scoped Authentication Administrator is sufficient |

## Role responsibility matrix

| **Task** | **Student** | **Teacher\(Scoped\)** | **School IT** | **Central IT** |
| --- | --- | --- | --- | --- |
| Enable TAP Policy | ❌ | ❌ | ❌ | ✅ |
| Create Administrative Units | ❌ | ❌ | ❌ | ✅ |
| Assign roles to teachers | ❌ | ❌ | ❌ | ✅ |
| Issue TAP for student | ❌ | ✅ own school | ✅ | ✅ |
| Use TAP to recover access | ✅ | ❌ | ❌ | ❌ |
| Delete expired TAPs | ❌ | ✅ own school | ✅ | ✅ |
| Manage tenant-wide auth policies | ❌ | ❌ | ❌ | ✅ |

## Known limitations and considerations

- Administrative Units can't be nested—you can't create a sub-AU for grade levels within a school AU.
- Groups added to an AU don't grant management of group members—students must be added as direct members of the AU \(not just their class group\) for teachers to manage them.
- TAP requires Microsoft Entra ID P1. Districts on Microsoft 365 A1 \(free for students\) need to upgrade or use delegated helpdesk password reset instead.
- TAP codes show only once. Teachers must copy and securely deliver them immediately upon creation.
- Security questions retire in March 2027. Begin migration now to avoid last-minute disruptions.

## Recommended migration timeline

| **Timeline** | **Milestone** |
| --- | --- |
| Now → June 2026 | Enable TAP policy, build Administrative Units, pilot at 1–2 schools |
| July → Sept 2026 | Roll out to all schools, train teachers on TAP issuance workflow |
| Oct 2026 → Feb 2027 | Full district deployment, monitor and tune policies |
| March 2027 | ✅ Security questions officially retired—district fully migrated |

## Reference links

- [Configure TAP in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-temporary-access-pass)
- [Administrative Units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)
- [Passwordless for Students – Microsoft 365 Education](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/protect-passwordless-students)
- [Security Questions Deprecation](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-security-questions)
- [Restricted Management Administrative Units](https://www.chanceofsecurity.com/post/microsoft-entra-restricted-management-administrative-units)
