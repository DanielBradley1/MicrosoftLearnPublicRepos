<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/school-data-sync -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Back to School transition - School Data Sync

The academic year transition process for School Data Sync \(SDS\) consists of the following steps:

[![Picture showing timeline of academic year transition for School Data Sync. Three weeks before end of school, review sync end date for your configuration. Two weeks after end of school, clean up your EDU tenant year to maintain a healthy tenant and keep administration manageable. We recommend running a standard cleanup. Ten weeks before school starts, prepare for the new school year. Two weeks before school starts, update SIS data, plan training, review new service add-ins, and allocate resources for BTS launch.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sds-academic-year-transition.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sds-academic-year-transition.png#lightbox)

## Review Sync end date

**Three weeks before the school year ends**, review the Sync end date for your connect data configuration by navigating to **Sync \| Configuration \| Connected data** tab.

You can find the Sync end date on **Sync \| Configuration \| Connected data** tab in the **Source** configuration section.

[![Screenshot showing SDS Sync Configuration page for managed data.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sds-sync-configuration-connect-data.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sds-sync-configuration-connect-data.png#lightbox)

## Clean up tenant

**Two weeks after the school year ends**, clean up the tenant from the prior year.

Clean up your tenant every year to maintain a healthy tenant and keep administration manageable. We advise running standard clean-up after sync end date is reached. To perform a group clean-up:

- Generate a section usage report
- Modify section usage report to include only classes you want to clean up
- Upload the report to the SDS Admin Center
- Select desired option \(Expired/archived\) and then run the cleanup

For detailed information:

- [Class / Section Group Cleanup](https://learn.microsoft.com/en-us/schooldatasync/azure-ad-group-cleanup)

We also recommend that you perform school [Security Groups and Administrative Units cleanup](https://learn.microsoft.com/en-us/schooldatasync/security-group-administrative-units-cleanup).

## Prepare for the new school year

**Ten weeks before the school year starts**, prepare the tenant for the upcoming school year.

After your tenant is cleaned up, it's time to prepare for the next school year.

Note

The following process doesn't require you to re-create your Manage data to Microsoft 365 configurations. The existing provision types and configurations persist after the following steps are completed. The next run starts processing the new academic session data based on your defined configurations. This makes the process easier, faster, and reduces complexity.

Prepping your connected data:

**If using CSV:**

- We recommend that you perform an initial inspection to ensure all the files are provided. Review that the expected files and columns are present and named correctly.
- If you're using Power Automate to upload CSV data, you should set the Power Automate flow to pause.
- If you're using Power Automate to upload CSV data, after the transition steps are completed, you'll need to [edit the Power Automate flow configuration to update the 'Id' value](https://learn.microsoft.com/en-us/schooldatasync/automate-csv-upload?tabs=configurepowerautomateflow#get-the-school-data-sync--connect-data-source--flow-id) before setting the Power Automate flow to resume.

**If using API:**

- Validate that the connection is available.
- If you updated your Client ID, make sure you have it available to update the connection credentials.
- You need to supply your Client Secret.

## Launch the new school year

**Two weeks before the school year starts**, launch the new school year.

To access the SDS Admin Portal, launch your web browser. Navigate to sds.microsoft.com, and then sign in.

- Begin [Academic Session transition](https://learn.microsoft.com/en-us/schooldatasync/academic-session-transition)
- Plan training
- Review new service add-ins
- Allocate/Plan resources for Back to School launch

## For support

If you need assistance:

- **SDS Support-** [**https://aka.ms/sdssupport**](https://aka.ms/sdssupport)

## Next steps

Next, let's take a look at Microsoft Teams and Microsoft 365 groups.

[Next: Microsoft Teams >](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/teams-microsoft-365-groups)
