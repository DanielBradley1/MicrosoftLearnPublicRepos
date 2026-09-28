<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/configure-assignments-for-teams -->
<!-- Sitemap-Last-Modified: 2026-02-20 -->

# Configure assignments for Teams

The content stored in SharePoint includes metadata and details about Assignments and Submissions that are stored for Assignments. The export user data is supported for both Student and Teacher users. However, delete data is only supported for Students due to co-mingling and data retention compliance. Teachers can delete their data in app by deleting assignments or classes. For more information, review the [Assignments Admin documentation](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-admin-documentation).

There are three scripts to use depending upon the scenario:

## Shared common step for Export and Delete user data scenario:

Use the [Get-UserClasses.ps1 script](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-get) to create a list of classes that user is part of. If the user left the class, then a text file containing those class IDs can be provided to include data from those classes. Otherwise data won't be exported or deleted from those classes. Running this script creates a csv file that contains a list of classes, the role of the user in class, and whether or not export or delete for the user was processed \(which is set to false by default\).

## Exporting User data:

Use the [Export-EDUAssignments.ps1 script](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-export) to export data for the user. The csv file generated in the above step is input to this script. Running this script will get assignments and submissions of each assignment and generates two files. The assignment file \(assignment.json\) contains assignments and submissions and report file\(GetAssignmentsReport.csv\) - status of running the script. After running the script, it updates the GetSubmissionsProcessed column in the csv input file to true for that specific class so that if there's a failure the script can be rerun.

## Deleting User data:

Use the [Delete-EDUAssignments.ps1 script](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-delete) to delete data for the user. The script reads the class details of user from input csv file generated in the previous shared step. It then deletes the submissions, and generates a report file\(DeleteAssignmentsReport.csv\) for status of running the script. When the deletion of submission is done it updates the DeleteSubmissionsProcessed column to true for that specific class, so that if there's a failure the script can be rerun. The script also removes students from the class unless optionally specified to not do so by the Tenant Admin, failing that the student will get all the assignments applicable to them be redistributed to them.
