<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-admin-documentation -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Assignments Admin Documentation

## Assignments

Assignments stores information that is generated both by teachers and students. All the data is co-shared between teacher and the specific student for which the information is intended in class. There are two stores of this, SharePoint and outside of SharePoint.

To view and manage Assignment settings, go to [Education > Assignment settings](https://admin.teams.microsoft.com/education/assignments-settings) in the Teams admin center.

Note

The same rules also apply to first-party integrations such as Reading Progress.

## Assignments data in SharePoint document libraries

Students' files associated with a Submission for Assignment are stored in a document library \(named: *Student Work*\). Files associated with Assignments that are created by teachers and accessible by Students are stored in another document library \(named: *Class Files*\) in the corresponding Class Team SharePoint site. First-party integrations may also store Assignments data in the same corresponding Class Team SharePoint site \(named: *Assignments title + time stamp*\).

### **Files associated with the student**

IT admins can use the Content Search tool to search for student files \(*Student Work*, *Class Files*, or other 1st-party integration files\) that are related to assignment submissions and files that are related to assignments. For example, an admin could search all SharePoint sites in the organization and use the student’s name and class or assignment name in the search query to find data relevant to a data subject request \(DSR\).

### **Files associated with the teacher**

IT admins can use the Content Search tool to search for teacher files \(*Student Work*, *Class Files*, or other 1st-party integration files\) that are related to assignments as well as files distributed to students by the teachers within a class on assignments. For example, an admin could search all SharePoint sites in the organization and use the teacher's name and class or assignment name in the search query to find data relevant to a DSR.

## Assignments data outside of SharePoint document libraries

Some data related to Assignments isn’t stored in the class team SharePoint site, which means it’s not discoverable with Content Search. This includes:

- Student grades and feedback from the teacher
- The list of documents submitted for an assignment by each student
- Assignment details like Due Date, etc.
- First-party integration data like Reading Progress passages or student pronunciation data

For this type of data, an IT admin or data owner, such as a teacher, may have to go into the Assignment in the class team to find data relevant to a DSR. The admin can add themselves as an owner to the class and view all the assignments for that class team.

Note

If a student is no longer part of the class, their data might still be present in the class as *no longer enrolled*. The student will have to provide the tenant admin the list of such classes that they were ever a part of.

## Bulk Export assignment data outside of SharePoint document libraries

### Bulk export for a student

To bulk export a single student's data, before removing the student from the classes they're a part of, [run the script](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/configure-assignments-for-teams) and provide the `userId`. If the student has been removed from the site, either the admin can add the student back to the class before running the script, or the admin can provide the `userId` and the `classId` that the student was ever a part of.

The data about the student submissions will be exported.

### Bulk export for a teacher

Bulk Export assignment data works the same way for a student, but all submissions that the teacher has access to will be exported.

## Bulk Delete assignment data outside of SharePoint document libraries

### Bulk delete for a student

To bulk delete a single student's data, before removing the student from the classes they're part of, [run the script](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/configure-assignments-for-teams) and provide the `userId`. If the student has been removed from the site, either the admin can add the student back to the class before running the script, or the admin can provide the `userId` and the `classId` that the student was ever a part of.

Providing a `ClassId` will allow the admin to only delete information about the student from a specific class.

### Bulk delet for a teacher

Since an assignment's data for a teacher is shared across the class, there's no bulk delete option. Instead the admin can add themselves to the class, go to the app, and delete the assignment.

For more information, see [Configure assignments for Teams](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/configure-assignments-for-teams).
