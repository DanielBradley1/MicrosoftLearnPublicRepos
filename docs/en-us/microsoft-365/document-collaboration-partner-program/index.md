<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/ -->
<!-- Sitemap-Last-Modified: 2025-06-25 -->

# Microsoft 365 Document Collaboration Partner Program overview

The Microsoft 365 Document Collaboration Partner Program \(MDCPP\) allows eligible communication and collaboration independent software vendors \(ISVs\) to integrate Microsoft 365 experiences into their platforms. Users of partner platforms would be able to share, edit, and coauthor Microsoft 365 documents without switching between apps or losing context.

Important

The Microsoft 365 Document Collaboration Partner Program is for independent software vendors \(ISVs\) whose business is document collaboration. It isn't open to Microsoft 365 customers directly.

The program makes integration with the following experiences available.

- [**Office for the Web**](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/office-for-the-web): Outside of a meeting experience, users can collaborate and edit Excel, PowerPoint, and Word documents from SharePoint and OneDrive for Business. To learn more about this experience in Teams, see [Edit a file in Microsoft Teams](https://support.microsoft.com/office/257a5e88-205a-4fb5-bbf1-c78c3e64de86).

  ![Office for the Web experience using Word.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/office-for-the-web-experience.png)
- **Live**: Meeting participants can interact and collaborate with PowerPoint Live and Excel Live.

  ![PowerPoint Live experience.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/powerpoint-live-experience.jpeg)

  - [PowerPoint Live experience](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/present): To learn more about the PowerPoint Live experience currently available in Teams, see [Present from PowerPoint Live in Microsoft Teams](https://support.microsoft.com/office/28b20e74-7165-499c-9bd4-0ad975d448ad).
  - [Excel Live experience](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/collaborate): To learn more about the Excel Live experience currently available in Teams, see [Excel Live in Microsoft Teams meetings](https://support.microsoft.com/office/a5790e42-7f75-4859-8674-cc3d07c86ede).

- [**Start Page**](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/start-page): Outside of a meeting experience, when users open the Excel, PowerPoint, and Word apps in your collaboration application without opening a specific file, they'll see recent files and templates for the Office app they opened.

  ![Start Page experience in the Word app in Teams.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/start-page-experience-word.png)

## Integrate experiences

To integrate these experiences into your collaboration application, do the following:

1. Be a member of the Microsoft 365 Document Collaboration Partner Program. Currently, the program is only available to cloud communication and collaboration partners. To learn more about the program, including how to apply, see [Apply for the Microsoft 365 Document Collaboration Partner Program](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/get-started/apply-for-mdcpp).
2. Set up your Azure app with the [appropriate permissions](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration).
3. Install the [@microsoft/document-collaboration-sdk](https://aka.ms/MDCPP-npm-package) npm package.
4. [Set up your environment to enable integration.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-environment)
