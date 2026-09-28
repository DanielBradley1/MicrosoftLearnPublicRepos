<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/baseline-reference-sis -->
<!-- Sitemap-Last-Modified: 2026-08-27 -->

# Student information system \(SIS\)

A student information system \(SIS\) is a software application or platform used by educational institutions to manage and store student data. SIS platforms handle core administrative tasks such as enrollment, attendance, grades, schedules, transcripts, and demographic information. They provide tools for educators, administrators, students, and parents to access and update student records, supporting efficient school operations and data-driven decision-making. Examples of SIS platforms include PowerSchool, Infinite Campus, and Skyward.

## Examples of Student Information Systems Worldwide

| SIS Name | Region/Country | Website |
| --- | --- | --- |
| PowerSchool | North America, Global | [powerschool.com](https://www.powerschool.com/) |
| Infinite Campus | United States | [infinitecampus.com](https://www.infinitecampus.com/) |
| Skyward | United States, Global | [skyward.com](https://www.skyward.com/) |
| SIMS | United Kingdom | [ess-sims.co.uk](https://www.ess-sims.co.uk/) |
| Arbor Education | United Kingdom | [arbor-education.com](https://arbor-education.com/) |
| Synergy SIS | United States, Global | [edupoint.com](https://www.edupoint.com/) |
| eSchoolPLUS | United States | [powerschool.com/eschoolplus](https://www.powerschool.com/eschoolplus) |
| ManageBac | International | [managebac.com](https://www.managebac.com/) |
| iSAMS | International | [isams.com](https://www.isams.com/) |
| Sentral | Australia | [sentral.com.au](https://www.sentral.com.au/) |
| Ed-admin | Africa, Middle East | [ed-admin.com](https://www.ed-admin.com/) |
| OpenSIS | Global \(Open Source\) | [opensis.com](https://www.opensis.com/) |
| Wisenet | Asia-Pacific, Global | [wisenet.co](https://www.wisenet.co/) |
| FACTS SIS | United States, Global | [factsmgt.com](https://factsmgt.com/) |

## Using Microsoft Fabric and School Data Sync to aggregate SIS information

Microsoft Fabric and School Data Sync \(SDS\) can be used together to aggregate and analyze data from multiple Student Information Systems \(SIS\).

- **School Data Sync \(SDS\):** SDS connects SIS platforms to Microsoft 365 Education, automating the synchronization of student, teacher, class, and roster information. It supports integration with many SIS platforms using APIs or CSV files.
- **Microsoft Fabric:** Fabric provides a unified analytics platform where data from SDS and other sources can be ingested, transformed, and visualized. By bringing SIS data into Fabric, schools and districts can create dashboards, generate reports, and gain insights into student performance, attendance, and other key metrics.

**Typical workflow:**

1. SDS imports and standardizes data from one or more SIS platforms.
2. The synchronized data is made available in Microsoft 365 and can be exported to Microsoft Fabric.
3. In Fabric, data engineers and analysts can aggregate, analyze, and visualize SIS data for decision-making and reporting.

This approach enables educational institutions to centralize student information, improve data-driven decisions, and streamline administrative processes.
