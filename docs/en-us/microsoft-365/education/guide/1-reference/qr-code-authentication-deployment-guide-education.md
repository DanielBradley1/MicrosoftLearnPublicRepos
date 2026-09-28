<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/qr-code-authentication-deployment-guide-education -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# QR code authentication deployment guide for education

## Overview and purpose

Microsoft Entra ID QR Code Authentication reached general availability in September 2025. Originally designed for frontline workers on shared devices, it maps perfectly to K-12 education environments where students share classroom tablets or mobile devices and can't be expected to remember complex usernames or passwords.

As Microsoft retires security questions for self-service password reset \(SSPR\) in March 2027, QR code authentication provides a modern, no-phone, no-password replacement. Each student receives a unique printed QR code - attachable to a badge, lanyard, or folder - paired with a short numeric PIN only they know. Sign-in takes seconds: scan the code, enter the PIN, done.

**How it works:**

- QR Code - serves as the student's unique identifier \(printed, not memorized\)
- Numeric PIN - the student's private credential \(8+ digits, numbers only\)
- No mobile device, no email address, no phone number required
- Works on shared iOS/iPadOS \(15.0+\) and Android classroom devices via Microsoft Teams
- Replaces security questions \(retiring March 2027\) as a no-device sign-in option

## Architecture overview

This solution uses the same hierarchical delegation model as the TAP deployment:

| **Level** | **Role** | **Capability** |
| --- | --- | --- |
| District Tenant | Central IT \(Global Admin\) | Enable QR code policy, create AUs, assign scoped roles |
| Administrative Unit | School-Level IT / Office Staff | Manage students and staff within their school only |
| Authentication Admin \(Scoped\) | Teachers / Building Admins | Generate and reset QR codes for students within their school AU only |
| Student Account | Student | Scan QR code + enter PIN to sign in—no phone or password needed |

Note

**Key principle:** Teachers can only generate or reset QR codes for students within their own school's Administrative Unit. They can't affect students at other schools or access district-wide settings.

## Prerequisites

| **Requirement** | **Details** |
| --- | --- |
| License | Microsoft 365 F1/F3, Microsoft Entra ID P1/P2, EMS E3/E5, or Office 365 F3\(Included in Microsoft 365 A3/A5 for Education\) |
| Central IT Role | Authentication Policy Administrator or Global Administrator |
| Teacher Role \(scoped\) | Authentication Administrator scoped to the school's AU |
| Shared Devices | iOS/iPadOS \(15.0+\) or Android devices with Microsoft Teams installedAndroid Teams: v1.0.0.2024143204 or lateriOS Teams: v1.0.0.77.2024132501 or later |
| Printer | Capable of printing QR codes at minimum 2" x 2" \(approx. 5cm x 5cm\) |
| Admin Center Access | [https://entra.microsoft.com](https://entra.microsoft.com) |

## Phase 1 – Enable the QR Code Authentication Policy \(Central IT\)

**This is a one-time tenant-wide configuration performed by Central IT.**

### Step 1: Enable QR code authentication in authentication methods

1. Sign in to [https://entra.microsoft.com](https://entra.microsoft.com) as Authentication Policy Administrator or higher.
2. Go to **Protection** > **Authentication methods** > **Policies**.
3. Select **QR code** from the list.
4. Select **Enable and target → Add target**.
5. Select the student security group \(for example, All-Students\) or **All users**.
6. Select the **Configure** tab and apply the recommended K-12 settings shown in the following table.
7. Select **Save**.

| **Setting** | **Recommended Value \(K-12\)** | **Reason** |
| --- | --- | --- |
| PIN Length | Eight digits \(minimum\) | Balances security with memorability for younger students |
| Standard QR Code Lifetime | 180 days \(one semester\) | Allows reissuance at the start of each school semester |
| Temporary QR Code Lifetime | Four hours | For students who forgot their badge or QR code that day |
| PIN Complexity | Enforced \(default\) | Prevents simple sequences such as 12345678 or 11111111 |

Important

QR code authentication is DISABLED by default. After generation, the QR code image is displayed ONLY ONCE. It must be downloaded and printed immediately. It can't be retrieved later. A new QR code must be generated if the original is lost.

## Phase 2 – Create administrative units per school \(Central IT\)

Administrative units \(AUs\) restrict a teacher's administrative permissions to only the students in their school - they can't accidentally affect accounts at other schools.

### Step 2: Create an Administrative Unit for Each School

Repeat the following steps for each school in your district:

1. Sign in to [https://entra.microsoft.com](https://entra.microsoft.com) as Global Administrator or Privileged Role Administrator.
2. Navigate to **Identity → Overview → Administrative units**.
3. Select **+ Add**.
4. Name: AU - \[School Name\] \(for example, AU - Jefferson Elementary\).
5. Description: Students and staff for \[School Name\].
6. Set Membership type to Assigned \(or Dynamic - see the following tip\).
7. Select **Create**.

Tip

**Dynamic Membership:** For large districts, use Dynamic membership rules to auto-populate each AU. Example rule: user.department -eq "Jefferson Elementary" — all users with that department attribute are added automatically as students enroll or transfer.

### Step 3: Add Student Accounts to Each AU

**Option A - Manual \(small schools\):**

1. Open the AU \(for example, AU - Jefferson Elementary\).
2. Select **Members → + Add members**.
3. Search for and select all student accounts for that school.
4. Select **Select** to save.

**Option B - Dynamic Rule \(recommended for large districts\):**

1. When creating the AU, set Membership type to **Dynamic User**.
2. Set the membership rule: user.department -eq "Jefferson Elementary"
3. Ensure student accounts have the **Department** attribute set in Microsoft Entra ID \(or synced from on-premises Active Directory\).

## Phase 3 – Assign scoped authentication administrator role to teachers

Assigning this role gives teachers the ability to generate and manage QR codes, but only for students in their own school's administrative unit.

### Step 4: Assign the authentication administrator role scoped to the school AU

1. Go to the administrative unit \(for example, AU - Jefferson Elementary\).
2. Select **Roles and administrators**.
3. Select **+ Add assignment**.
4. Search for and select the role: **Authentication Administrator**.
5. Under **Select members**, add the teachers or a Teacher Security Group for that school \(for example, Jefferson-Elementary-Staff\).
6. Select **Add**.

**What the scoped Authentication Administrator role allows:**

| **Permission** | **Granted?** |
| --- | :---: |
| ✅ Generate QR codes for students in their AU | Yes |
| ✅ Issue temporary QR codes for students in their AU | Yes |
| ✅ Reset PINs for students in their AU | Yes |
| ❌ Manage Global Admins or Privileged Authentication Admins | No |
| ❌ Access students in other school AUs | No |
| ❌ Change tenant-wide authentication policies | No |

## Phase 4 – Teacher QR code issuance workflow \(school-level staff\)

Once configured, this section is the day-to-day process teachers follow to provision or replace a student's QR code.

### Step 5: Teacher generates a QR code for a student

1. Teacher signs in to [https://entra.microsoft.com](https://entra.microsoft.com) with their school staff account.
2. Go to **Identity** > **Users**.
3. Search for the student's name or username.
4. Select the student account.
5. Select **Authentication methods** from the left-hand menu.
6. Select **+ Add authentication method**.
7. Choose **QR code** from the dropdown.
8. A QR code image and a temporary PIN are generated and displayed on screen.
9. ⚠️ Download and print the QR code IMMEDIATELY. It can't be retrieved again after this screen.
10. Note the temporary PIN - the student must change it on their first sign-in.
11. Print the QR code at minimum 2" x 2" size and deliver to the student \(badge, lanyard, folder label\).
12. Communicate the temporary PIN to the student verbally or via a secure printed slip.

Important

**⚠️ Best Practice:** Never email or digitally send QR codes or PINs to students. Always deliver both in person. The QR code and PIN must be kept together - one is useless without the other. The student's PIN becomes private after their first sign-in and can't be retrieved by staff.

### Step 5b: Teacher issues a temporary QR code \(lost or forgotten badge\)

If a student forgets their QR code badge, you can issue a short-lived temporary QR code for that day:

1. Go to the student's **Authentication methods** in the Microsoft Entra admin center.
2. Select the existing QR code entry > **Edit**.
3. Enable **Temporary QR code**.
4. Set lifetime: up to 4 hours \(recommended for a school day\).
5. Download and print the temporary QR code.
6. Deliver to the student in person - it expires automatically after the configured duration.

## Phase 5 – Student sign-in experience

### Step 6: Student signs in using QR code + PIN

**Web Sign-In Experience \(Shared browser / device\):**

1. Student goes to [https://login.microsoft.com](https://login.microsoft.com) or opens any Microsoft 365 app.
2. Selects **Sign-in options**.
3. Selects **Sign in with a QR code**.
4. Scans their printed QR code by using the device camera or Microsoft Teams app.
5. Enters their numeric PIN.
6. First sign-in only: student is prompted to change the temporary PIN to a personal PIN \(only the student knows this PIN going forward\).
7. Student is signed in - no username or complex password is typed at any point.

**App-Based Sign-In \(Microsoft Teams on shared iOS/Android device\):**

1. Open Microsoft Teams on the shared classroom device.
2. Selects **Sign in with QR code**.
3. Scans QR code → Enters PIN → Student is signed in.

Important

**Device Compatibility:** QR code authentication currently works **only** on iOS/iPadOS \(15.0+\) and Android devices via the Microsoft Teams app. It doesn't work on Windows desktops, Mac computers, Chromebooks, or via barcode scanners. Plan shared device deployments accordingly.

## Phase 6 – Microsoft Graph API automation \(optional\)

For large districts, QR code generation can be automated via Microsoft Graph API—useful for bulk provisioning at the start of each school year or semester.

```
# Connect to Microsoft Graph
Connect-MgGraph -Scopes "UserAuthenticationMethod.ReadWrite.All"

# Generate a QR code authentication method for a student
$body = @{
    standardQRCode = @{
        lifetimeInDays = 180     # One school semester
    }
    pin = @{
        isTemporary = $true
        code        = "87654321"  # Temporary PIN — student changes on first login
    }
} | ConvertTo-Json -Depth 3

Invoke-MgGraphRequest -Method POST `
    -Uri "https://graph.microsoft.com/beta/users/jsmith@jeffersonelementary.edu/authentication/qrCodePinMethods" `
    -Body $body `
    -ContentType "application/json"
```

Tip

This script can be integrated with your Student Information System \(SIS\) to auto-provision QR codes for new students at enrollment — and auto-revoke codes for students who transfer or graduate.

## Security best practices

| **Practice** | **Recommendation** |
| --- | --- |
| QR Code Storage | Print and laminate — store in student folder or attach to ID badge/lanyard |
| Lost QR Code | Issue a temporary QR code immediately; revoke and re-issue the standard QR code |
| PIN Confidentiality | Student's PIN is known only to the student after first sign-in — staff can't retrieve it |
| QR Code Lifetime | Set to semester length \(180 days\) — re-issue at the start of each school semester |
| Audit Logs | Review QR code issuance and sign-in logs in Microsoft Entra ID → Audit Logs monthly |
| Teacher Role Hygiene | Remove Authentication Administrator role from staff who leave the school |
| Conditional Access | Scope QR code sign-in to trusted school network IP ranges via a Conditional Access policy |
| No Sharing | Each QR code is unique to one student — sharing QR codes is a security violation |

## Role responsibility matrix

| **Task** | **Student** | **Teacher\(Scoped\)** | **School IT** | **Central IT** |
| --- | --- | --- | --- | --- |
| Enable QR Code Auth Policy | ❌ | ❌ | ❌ | ✅ |
| Create Administrative Units | ❌ | ❌ | ❌ | ✅ |
| Assign roles to teachers | ❌ | ❌ | ❌ | ✅ |
| Generate QR code for student | ❌ | ✅ own school | ✅ | ✅ |
| Issue temporary QR code | ❌ | ✅ own school | ✅ | ✅ |
| Reset student PIN | ❌ | ✅ own school | ✅ | ✅ |
| Sign in using QR code + PIN | ✅ | ❌ | ❌ | ❌ |
| Manage tenant-wide auth policies | ❌ | ❌ | ❌ | ✅ |

## Known limitations and considerations

- QR code authentication is supported ONLY on iOS/iPadOS \(15.0+\) and Android — not Windows desktops, Mac computers, or Chromebooks.
- Microsoft Teams app must be installed on shared devices at the minimum required versions \(Android: 1.0.0.2024143204+ \| iOS: 1.0.0.77.2024132501+\).
- The QR code image is displayed ONLY ONCE at generation. It must be downloaded and printed immediately. A new QR code must be generated if the original is lost.
- QR code authentication is a single-factor method \(QR code + PIN\), not full MFA. Use Conditional Access policies to enforce more controls for sensitive applications.
- Students can't self-service reset their PIN. A scoped teacher or admin must reset it via the Microsoft Entra admin center.
- Administrative Units can't be nested. You can't create sub-AUs for grade levels within a school AU.
- License required per user: Microsoft 365 F1/F3, Microsoft Entra ID P1/P2, EMS E3/E5, or Office 365 F3 \(included in Microsoft 365 A3/A5 for Education\).
- Temporary QR codes have a maximum lifetime of 12 hours.

## Recommended migration timeline

| **Timeline** | **Milestone** |
| --- | --- |
| Now → June 2026 | Enable QR code policy, build Administrative Units, pilot at 1–2 schools |
| July → Sept 2026 | Roll out to all schools, print and distribute QR codes, train teachers on issuance workflow |
| Oct 2026 → Feb 2027 | Full district deployment, monitor sign-in logs and tune policies |
| March 2027 | ✅ Security questions officially retired—district fully migrated to QR code authentication |

## Reference links

- [QR Code Authentication Method in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-qr-code)
- [How to Enable QR Code Authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-qr-code)
- [Administrative Units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)
- [Passwordless for Students – Microsoft 365 Education](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/protect-passwordless-students)
