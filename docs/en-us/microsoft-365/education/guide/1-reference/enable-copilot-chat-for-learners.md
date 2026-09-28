<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/enable-copilot-chat-for-learners -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# Enable Copilot Chat for learners

Copilot Chat is available by default to adult learners, including higher education students. In K-12 Education tenants, it is **off** by default for students ages 13-17. An IT administrator must classify the tenant and set each student's age group before those students can use Copilot Chat, Study and Learn, and Copilot Notebooks \(including Study Guide\). Students under 13 cannot access Copilot Chat.

## Key resources

- [Enable Copilot Chat tutorial video](https://aka.ms/enablecopilotchatvideo)
- [Tenant identifier setting](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-identifier)
- [Age group setting](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group)

## Before you begin

- Sign in as a Global Administrator.
- Confirm that intended users have an eligible Microsoft 365 Education A1, A3, or A5 student license.
- Watch the [Copilot Chat setup tutorial for IT administrators](https://aka.ms/enablecopilotchatvideo).

## Step 1: Set the Education Tenant Identifier

1. Open the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. Select **Show all > Settings > Org settings > Services**.
3. Select **Microsoft Education Tenant Identifier**.
4. Choose the setting that matches your institution:

   - K-12 for a school, district, or ministry of education
   - Higher Education for a college, university, technical school, or other post-secondary institution.

5. Select **Save**.

See [Set the Education Tenant Identifier](https://aka.ms/enablecopilotchattenantidentifier) for complete guidance.

Higher Education tenants treat students as adults by default. If your institution has younger students, set their age group explicitly so the correct access policy applies.

## Step 2: Set student age groups in a K-12 tenant

In a K-12 tenant, assign an AgeGroup value to each student account:

| **Value** | **Typical age** | **Copilot Chat access** |
| --- | --- | --- |
| **minor** | Under 13 | Blocked |
| **notAdult** | 13-17 | Allowed |
| **adult** | 18 or older | Allowed |

To update students in bulk:

1. In the Microsoft 365 admin center, go to **Settings > Org settings > Services > Microsoft Education**.
2. Under **Manage student age groups**, select **Download users**.
3. In the downloaded CSV, keep the header row and these columns:

   - User principal name
   - AgeGroup

4. Enter the appropriate age group value for each student and save the file as **Users.csv**.
5. Under **Manage student age groups**, select **Upload users**, choose the CSV, and select **Continue**.
6. After processing finishes, download the users again and confirm that the values were applied correctly.

The bulk-upload workflow also grants the required **Consent provided for minor** value. If you update accounts individually in Microsoft Entra ID, through Microsoft Graph, or with PowerShell, set the required consent value as well.

See [Set Student Age Group](https://aka.ms/enablecopilotchatstudentagegroup) for individual-user, bulk, School Data Sync, Microsoft Graph, and PowerShell options.

## Step 3: Verify access

Changes are processed asynchronously and may take time to appear. After processing completes:

1. Confirm the updated values by downloading the user list again.
2. Test sign-in with representative accounts for each age group used by your institution.
3. Open Microsoft Copilot on the web or Windows desktop and confirm that Copilot Chat and Study and Learn are available to eligible users.
4. Confirm that accounts marked minor remain blocked.
