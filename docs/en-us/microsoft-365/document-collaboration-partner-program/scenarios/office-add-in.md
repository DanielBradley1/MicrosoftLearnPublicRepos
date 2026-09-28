<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/office-add-in -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Use an Office Add-in to facilitate integration between an Office file and your app

With an [Office Add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/overview/office-add-ins), you can provide the user with the ability to open your app directly from a [ribbon button](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-in-commands) in an Office document. In a collaboration app, this means that the user can share the Office document with others for presenting in a meeting or asynchronous collaboration and coauthoring, functionality that's available through the MDCPP for Excel, PowerPoint, and Word documents hosted in SharePoint and OneDrive for Business.

An Office Add-in can be great for integrating with the following scenarios. The user can select your app's button in the Office ribbon. That action would open the current Office document in your web app. You may also be able to set up the action to open in the desktop version of your collaboration app, if your app supports that functionality.

- [Present-live experiences](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/present): From a PowerPoint presentation file, share in a meeting using your collaboration app.
- [Collaborate-live experiences](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/collaborate): From an Excel workbook file, share in a meeting using your collaboration app.
- [Coauthoring on the web](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/office-for-the-web): From an Excel, PowerPoint, or Word file, open in your collaboration app for users to coauthor.

Important

Using an Office Add-in to integrate between an Office file and your app doesn't require MDCPP membership, so this approach can also be used by non-collaboration apps.

## Prerequisites

- The Excel, PowerPoint, or Word file must support Office Add-ins.
- The app must be able to obtain a valid user token to the OneDrive for Business or SharePoint resource.
- The user has been signed in with a Microsoft 365 account.

## Example

1. To create a basic Office Add-in project, you can complete one of the following quick starts. Be sure to select the **Add-in only manifest** option when you're creating the project.

   - [Excel](https://learn.microsoft.com/en-us/office/dev/add-ins/quickstarts/excel-quickstart-jquery)
   - [PowerPoint](https://learn.microsoft.com/en-us/office/dev/add-ins/quickstarts/powerpoint-quickstart-yo)
   - [Word](https://learn.microsoft.com/en-us/office/dev/add-ins/quickstarts/word-quickstart-yo)

2. Open the **./manifest.xml** and update the various properties to use your app's name instead of Contoso, more appropriate descriptions, etc. \(examples as follows\). However, keep the localhost URLs for now.

   ```xml
   <ProviderName>Contoso</ProviderName>
   <DisplayName DefaultValue="My Contoso Office Add-in"/>
   <Description DefaultValue="Share this file in Contoso."/>
   ...
   <bt:String id="FunctionButton.Label" DefaultValue="Share in Contoso"/>
   ...
   <bt:String id="GetStarted.Description" DefaultValue="Your sample add-in loaded successfully. Go to the HOME tab and click the 'Share in Contoso' button to get started."/>
   <bt:String id="FunctionButton.Tooltip" DefaultValue="Click to Share in Contoso"/>
   ```

3. Still in the manifest file, update the first `<Hosts>` entry to appear as follows. Include a `<Host>` entry for "Document" if your add-in should support Word, "Presentation" for PowerPoint, and "Workbook" for Excel.

   ```xml
   <Hosts>
       <Host Name="Document"/>
       <Host Name="Presentation"/>
       <Host Name="Workbook"/>
   </Hosts>
   ```

4. Continuing in the manifest file, update the second `<Hosts>` node to appear as follows. Include a `<Host>` entry for "Document" if your add-in should support Word, "Presentation" for PowerPoint, and "Workbook" for Excel.

   ```xml
   <Hosts>
     <Host xsi:type="Document">
       <DesktopFormFactor>
         <GetStarted>
           <Title resid="GetStarted.Title"/>
           <Description resid="GetStarted.Description"/>
           <LearnMoreUrl resid="GetStarted.LearnMoreUrl"/>
         </GetStarted>
         <FunctionFile resid="Commands.Url"/>
         <ExtensionPoint xsi:type="PrimaryCommandSurface">
           <OfficeTab id="TabHome">
             <Group id="CommandsGroup">
               <Label resid="CommandsGroup.Label"/>
               <Icon>
                 <bt:Image size="16" resid="Icon.16x16"/>
                 <bt:Image size="32" resid="Icon.32x32"/>
                 <bt:Image size="80" resid="Icon.80x80"/>
               </Icon>
               <Control xsi:type="Button" id="FunctionButton">
                 <Label resid="FunctionButton.Label"/>
                 <Supertip>
                   <Title resid="FunctionButton.Label"/>
                   <Description resid="FunctionButton.Tooltip"/>
                 </Supertip>
                 <Icon>
                   <bt:Image size="16" resid="Icon.16x16"/>
                   <bt:Image size="32" resid="Icon.32x32"/>
                   <bt:Image size="80" resid="Icon.80x80"/>
                 </Icon>
                 <Action xsi:type="ExecuteFunction">
                   <FunctionName>action</FunctionName>
                 </Action>
               </Control>
             </Group>
           </OfficeTab>
         </ExtensionPoint>
       </DesktopFormFactor>
     </Host>
     <Host xsi:type="Presentation">
       <DesktopFormFactor>
         <GetStarted>
           <Title resid="GetStarted.Title"/>
           <Description resid="GetStarted.Description"/>
           <LearnMoreUrl resid="GetStarted.LearnMoreUrl"/>
         </GetStarted>
         <FunctionFile resid="Commands.Url"/>
         <ExtensionPoint xsi:type="PrimaryCommandSurface">
           <OfficeTab id="TabHome">
             <Group id="CommandsGroup">
               <Label resid="CommandsGroup.Label"/>
               <Icon>
                 <bt:Image size="16" resid="Icon.16x16"/>
                 <bt:Image size="32" resid="Icon.32x32"/>
                 <bt:Image size="80" resid="Icon.80x80"/>
               </Icon>
               <Control xsi:type="Button" id="FunctionButton">
                 <Label resid="FunctionButton.Label"/>
                 <Supertip>
                   <Title resid="FunctionButton.Label"/>
                   <Description resid="FunctionButton.Tooltip"/>
                 </Supertip>
                 <Icon>
                   <bt:Image size="16" resid="Icon.16x16"/>
                   <bt:Image size="32" resid="Icon.32x32"/>
                   <bt:Image size="80" resid="Icon.80x80"/>
                 </Icon>
                 <Action xsi:type="ExecuteFunction">
                   <FunctionName>action</FunctionName>
                 </Action>
               </Control>
             </Group>
           </OfficeTab>
         </ExtensionPoint>
       </DesktopFormFactor>
     </Host>
     <Host xsi:type="Workbook">
       <DesktopFormFactor>
         <GetStarted>
           <Title resid="GetStarted.Title"/>
           <Description resid="GetStarted.Description"/>
           <LearnMoreUrl resid="GetStarted.LearnMoreUrl"/>
         </GetStarted>
         <FunctionFile resid="Commands.Url"/>
         <ExtensionPoint xsi:type="PrimaryCommandSurface">
           <OfficeTab id="TabHome">
             <Group id="CommandsGroup">
               <Label resid="CommandsGroup.Label"/>
               <Icon>
                 <bt:Image size="16" resid="Icon.16x16"/>
                 <bt:Image size="32" resid="Icon.32x32"/>
                 <bt:Image size="80" resid="Icon.80x80"/>
               </Icon>
               <Control xsi:type="Button" id="FunctionButton">
                 <Label resid="FunctionButton.Label"/>
                 <Supertip>
                   <Title resid="FunctionButton.Label"/>
                   <Description resid="FunctionButton.Tooltip"/>
                 </Supertip>
                 <Icon>
                   <bt:Image size="16" resid="Icon.16x16"/>
                   <bt:Image size="32" resid="Icon.32x32"/>
                   <bt:Image size="80" resid="Icon.80x80"/>
                 </Icon>
                 <Action xsi:type="ExecuteFunction">
                   <FunctionName>action</FunctionName>
                 </Action>
               </Control>
             </Group>
           </OfficeTab>
         </ExtensionPoint>
       </DesktopFormFactor>
     </Host>
   </Hosts>
   ```

5. Save your changes to the manifest file.
6. Replace the contents of the **./src/commands/commands.js** with the following JavaScript code, then save the file. The code uses the [Document.getFilePropertiesAsync JavaScript API](https://learn.microsoft.com/en-us/javascript/api/office/office.document#office-office-document-getfilepropertiesasync-member\(1\)) to get the document's URL.

   ```javascript
   Office.onReady(() => {
     // If needed, Office.js is ready to be called.
   });

   /**
    * Opens the collaboration app in the default browser and passes along the URL of the current file.
    * @param event {Office.AddinCommands.Event}
    */
    async function action(event) {
     // Get the URL of the current file.
     Office.context.document.getFilePropertiesAsync(function (asyncResult) {
       const fileProperties = asyncResult.value;
       const fileUrl = fileProperties.url;
       if (fileUrl === "") {
         console.log("The file hasn't been saved yet. Save the file and try again.");
       } else {
         console.log(fileUrl);

         // Add code here that confirms the file is located in SharePoint or OneDrive for Business.

         // Use your app's URL here.
         const collaborationAppUrl = "https://bing.com";

         // Configure URL with appropriate security, parameter names, etc.
         window.open(collaborationAppUrl + "?docUrl=" + encodeURIComponent(fileUrl), "_blank");
       }
     });

     // Calling event.completed is required. event.completed lets the platform know that processing has completed.
     event.completed();
   }

   // Register the function with Office.
   Office.actions.associate("action", action);
   ```

7. By default, running the add-in opens in the Office application of the quick start you created. For a different Office app, open the **./package.json** file and set the "app\_to\_debug" value to "excel", "powerpoint", or "word" as preferred. Save your changes.
8. Run the command that opens Office and sideloads the add-in \(see the quick start's instructions\), then select the **Share in Contoso** ribbon button on the **Home** tab.

Note

The add-in project includes task pane files. This example doesn't use the task pane, so you can remove the task pane files found in the **./src** folder and any config or other code that reference the task pane.
