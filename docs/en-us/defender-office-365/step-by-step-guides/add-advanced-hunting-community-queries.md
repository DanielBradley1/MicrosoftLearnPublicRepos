<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/add-advanced-hunting-community-queries -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Add Advanced Hunting community queries to Microsoft Defender and Microsoft Sentinel

You can create and share Advanced Hunting queries in Microsoft Defender. Shared queries help your own security work and help other Defender users find threats.

This guide shows you how to create or modify queries. You then publish them to the **Community queries** section in the Microsoft Defender portal. When you share queries, other customers can detect threats faster. This drives collaboration across the security community.

[![Screenshot of community queries in Advanced Hunting in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-in-advanced-hunting.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-in-advanced-hunting.png#lightbox)

## Prerequisites

- A GitHub account.
- This article uses [Visual Studio Code](https://code.visualstudio.com/) \(VS Code\) to fork, clone, create, and sync queries with the Azure Sentinel GitHub repository. You can also use other tools, but the steps might differ.
- A Microsoft 365 subscription that includes Advanced Hunting. For example:

  - Microsoft Defender
  - Microsoft Sentinel
  - Microsoft Defender for Office 365 Plan 2

## Step 1: Fork the Azure Sentinel GitHub repository to your GitHub account

Because you don't have admin permissions to the Azure Sentinel GitHub repository, you need to fork the repository, and the only available destination is your GitHub account.

1. Open the Azure Sentinel GitHub repository at [https://github.com/Azure/Azure-Sentinel/](https://github.com/Azure/Azure-Sentinel/).
2. Select **Fork** to create your own copy of the repository. On the **Create a new fork** page that opens, review the following default settings:

   - **Owner**: Verify your GitHub account name is shown.
   - **Repository name**: Verify the value **Azure-Sentinel**.
   - **Description**: Verify the description text.
   - **Copy the main branch only**: Verify this option is selected.


   When you're finished on the **Create a new fork page**, select **Create new fork**.


   [![Screenshot of the top of the Azure Sentinel GitHub repository with Fork selected.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-fork-repo.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-fork-repo.png#lightbox)


   [![Screenshot of the Create a new fork page.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-create-new-fork.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-create-new-fork.png#lightbox)

3. After the fork is successfully created, you're taken to the URL of the Azure-Sentinel repository fork in your GitHub account: `https://github.com/<YourGitHubAccountName>/Azure-Sentinel`. On this page, select **Code**. On the **Local** tab of the drop-down that opens, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/github-copy-url-to-clipboard-icon.png) **Copy url to clipboard** from the **HTTPS** tab of the **Clone** section. The copied URL is: `https://github.com/<YourGitHubAccountName>/Azure-Sentinel.git`.

   [![Screenshot of Copy url to clipboard from the Code button on your forked copy of the Azure-Sentinel page.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-clone-fork.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-clone-fork.png#lightbox)

## Step 2: Clone the GitHub repository to your local computer

After you fork the Azure Sentinel GitHub repository to your GitHub account, you need to create a local clone of the repository on your computer to work out of.

1. Open VS Code. If you're not already in a clean session without other files opened, select **File** > **New Window** or press CTRL+Shift+N.
2. Select **Source Control** or press CTRL+Shift+G

   [![Screenshot of Visual Studio Code with Source Control selected.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control.png#lightbox)
3. In the **Source Control** flyout that opens, select **Clone Repository**.

   [![Screenshot of Clone Repository in Visual Studio Code with Clone Repository selected.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-repo.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-repo.png#lightbox)
4. In the dialog that opens, paste the `https://github.com/<YourGitHubAccountName>/Azure-Sentinel.git` URL you copied from your forked GitHub repository page into the box, and then select **Clone from URL** that appears beneath the box.

   [![Screenshot of the Clone Repository dialog in Visual Studio Code with the forked GitHub URL entered and Clone from URL selected.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-from-url.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-from-url.png#lightbox)
5. In the **Choose a folder to clone `https://github.com/<YourGitHubAccountName>/Azure-Sentinel.git` into** dialog that opens, find or create a local parent folder \(for example, `C:\GitHub`\) for the cloned fork of the repository, and then select **Select as Repository Destination**. The local clone of the forked repository is contained in the `<ParentFolder>\<RepositoryName>` folder \(for example, `C:\GitHub\Azure-Sentinel`\).

   [![Screenshot of the Choose a folder to clone into dialog with a destination parent folder selected and highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-cloned-repo-destination.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-cloned-repo-destination.png#lightbox)
6. Wait several minutes for the cloning of the Azure-Sentinel repository to complete.

   [![Screenshot of the progress dialog in Visual Studio Code as the Azure-Sentinel repository is being cloned.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-cloning-repo.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-cloning-repo.png#lightbox)
7. After cloning completes, a **Would you like to open the clone repository?** dialog opens. Select **Open** to open the cloned repository in VS Code \(for example, the `C:\GitHub\Azure-Sentinel` folder and its contents\).

   [![Screenshot of the Would you like to open the clone repository? dialog from Visual Studio Code dialog that opens after cloning the repository completes, with Open highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-open-cloned-repo.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-open-cloned-repo.png#lightbox)
8. If you recently created the folder structure on your local drive, you might receive a **Do you trust the authors of the files in this folder?**, which refers to the `Azure-Sentinel` folder \(you trust them\).

   To trust any future repositories that you clone in the parent folder \(for example, `C:\GitHub`\), select **Trust the authors of all files in the parent folder `<ParentFolderName>`**.

   To continue, select **Yes, I trust the authors**.

   [![Screenshot of the Do you trust the authors of the files in this folder? dialog from Visual Studio Code dialog that might open, with Yes, I trust the authors highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-trust-authors.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-trust-authors.png#lightbox)

## Step 3: Create a working branch in the cloned repository on your local computer

After you select **Yes, I trust the authors**, VS Code opens in **Explorer** view with the `Azure-Sentinel` folder selected. You can see all files and folders from the parent repository on GitHub.

By default the **master** \(main\) branch is active when you open your cloned fork of the repository. Don't make updates in the **master** branch. Instead, create a working branch in your locally cloned, forked copy of the repository to work out of.

1. In VS Code, select the active branch name in the bottom left corner \(which is likely **master**\).

   [![Screenshot of the active \(open\) branch highlighted in Visual Studio Code.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-select-active-branch.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-select-active-branch.png#lightbox)
2. In the dialog that opens, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Create new branch from...**, and then select **master** \(other available branches also appear in the branch list\).

   [![Screenshot of the dialog that opens after you select the active \(open\) branch in Visual Studio Code with Create new branch from... highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-create-new-branch-from.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-clone-create-new-branch-from.png#lightbox)

   [![Screenshot of the dialog that opens after you select Create new branch from... in Visual Studio Code with the master branch highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-create-new-branch-from-master.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-create-new-branch-from-master.png#lightbox)
3. In the **Please provide a new branch name** dialog that opens, enter a suitable name for the branch \(for example, `new-mdo-queries`\), and then press Enter to confirm.

   [![Screenshot of the Please provide a new branch name dialog that opens in Visual Studio Code, with the value new-mdo-queries entered.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-enter-new-branch-name.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-enter-new-branch-name.png#lightbox)

The active branch changes from **master** to the new branch you created.

To separate your work on different queries, you can create multiple working branches with different names by repeating the previous steps in this section.

Next, create or modify Advanced Hunting queries in your working branch as described in [Create Advanced Hunting queries in the working branch](#step-4-create-advanced-hunting-queries-in-the-working-branch-in-the-cloned-repository-on-your-local-computer).

## Step 4: Create Advanced Hunting queries in the working branch in the cloned repository on your local computer

When you open VS Code to create or update queries, always verify your desired working branch is the active branch \(not **master**\):

[![Screenshot of the active \(open\) branch highlighted in Visual Studio Code, which is now the new branch that you created in the previous step.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-verify-active-branch.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-verify-active-branch.png#lightbox)

If it isn't, select the active branch name in the bottom left corner, and then select the working branch from the **branches** section.

1. Now you can create hunting queries in your working branch. For example, the following Kusto Query Language \(KQL\) query is a basic report of recipients who receive the most phishing messages.

   ```kusto
   EmailEvents
   | where ThreatTypes has "Phish" and EmailDirection == "Inbound"
   | summarize count() by RecipientEmailAddress
   | sort by count_
   | top 15 by count_
   ```

2. Test the query on the **Advanced Hunting** page in the Defender portal at [https://security.microsoft.com/v2/advanced-hunting](https://security.microsoft.com/v2/advanced-hunting) to ensure the query contains no mistakes and it returns data as expected.

   [![Screenshot of the Advanced Hunting page in the Defender portal with the previous example query and results without error.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-test-query-in-advanced-hunting.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-test-query-in-advanced-hunting.png#lightbox)
3. In the **Explorer** view of VS Code, go to one of the following folders. The folder you choose depends on where you want the query to appear:

   - `\Azure-Sentinel\Hunting Queries\Microsoft 365 Defender\Email Queries`: Available in the **Community queries** section on the **Queries** tab of the **Advanced hunting** page in the Defender portal at [https://security.microsoft.com/v2/advanced-hunting](https://security.microsoft.com/v2/advanced-hunting).
   - `\Azure-Sentinel\Solutions\Microsoft Defender XDR\Hunting Queries\Email Queries`: Available as Sentinel queries \(Microsoft Defender XDR Solution\).


   In most cases, you should ultimately create the query file in both locations so you can use the query in both scenarios.

4. In VS Code, create a new .yaml file in the appropriate subfolder under `\Azure-Sentinel\Hunting Queries\Microsoft 365 Defender\Email Queries` or `\Azure-Sentinel\Solutions\Microsoft Defender XDR\Hunting Queries\Email Queries`. There are many subfolders to choose from. In our example, a logical name and location for our new query file is `Top users receiving phish.yaml` in the `Phish` subfolder.

   You can find more information on the requirements and structure of the .yaml file at [Query Style Guide](https://github.com/Azure/Azure-Sentinel/wiki/Query-Style-Guide) on the Azure-Sentinel repository wiki.

   Use the [New-Guid](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/new-guid) cmdlet in Windows PowerShell to create a unique GUID for the **id** property of the query file \(for example, 36f68d74-3e45-44d8-9915-0d35b7567bcf\).

   The finished `Top users receiving phish.yaml` file looks something like the following example. The `query` field contains the KQL query body that counts inbound phishing messages by recipient:

   ```yml
   id: 36f68d74-3e45-44d8-9915-0d35b7567bcf
   name: Friendly name describing the query
   description: |
     A short description of what the query does.
   description-detailed: |
     A much longer description of the intention of the query within Defender for Office 365.
   requiredDataConnectors:
   - connectorId: MicrosoftThreatProtection
     dataTypes:
     - EmailEvents
   tactics:
     - InitialAccess
   relevantTechniques:
     - T1566
   query: |
     EmailEvents
     | where ThreatTypes has "Phish" and EmailDirection == "Inbound"
     | summarize count() by RecipientEmailAddress
     | sort by count_
     | top 15 by count_
   version: l.0.0
   ```

5. After you complete and save the query file in one of the two query folders \(`\Azure-Sentinel\Hunting Queries\...` or `\Azure-Sentinel\Solutions\...`\), copy the file to the other query folder so you can use the query in both Advanced Hunting and Microsoft Sentinel.

## Step 5: Synchronize the changes from your local computer to the fork in your GitHub account

After you add .yaml query files on your local computer, sync those updates back to your fork on GitHub.

1. In VS Code, select the **Source Control** view.

   [![Screenshot of Visual Studio Code with the Source Control view highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-select-source-control.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-select-source-control.png#lightbox)
2. In the dialog that opens, a **Changes** section lists all files modified in the current branch:

   [![Screenshot of the Source Control view in Visual Studio Code with Changes highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-changes.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-changes.png#lightbox)

   - If you click on the filename, the modified file opens with the modified text highlighted. You can review the changes for issues or mistakes before you continue.
   - In the **Message** box, enter a brief description of the changes. Use concise language. For example, **Added a query to list top Phish recipients**. When you're finished, select **Commit**.

     [![Screenshot of the Source Control view in Visual Studio Code with the Message box filled out and the Commit button highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-message-and-commit.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-message-and-commit.png#lightbox)
   - If this is the first time you push this branch to your GitHub fork, select **Publish Branch**.

     [![Screenshot of the Source Control view in Visual Studio Code with the Publish Branch button highlighted.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-publish-branch.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-vs-code-source-control-publish-branch.png#lightbox)


   For later updates, select **Sync Changes** instead.

## Step 6: Create a pull request from the fork in your GitHub account to the public Azure Sentinel repository

After you synchronize the updates to the forked copy of the repository in your GitHub account, you then create a pull request to merge those changes back into the public Azure Sentinel GitHub repository.

Tip

As long as the pull request hasn't been merged, you can repeat [Create Advanced Hunting queries in the working branch](#step-4-create-advanced-hunting-queries-in-the-working-branch-in-the-cloned-repository-on-your-local-computer) and [Synchronize changes to your GitHub fork](#step-5-synchronize-the-changes-from-your-local-computer-to-the-fork-in-your-github-account) to update the source files in the forked copy of the repository, which modifies the active pull request.

1. Go to the `https://github.com/<YourGitHubAccountName>/Azure-Sentinel` link from [Fork the Azure Sentinel GitHub repository](#step-1-fork-the-azure-sentinel-github-repository-to-your-github-account).
2. If necessary, refresh the page to see the notification that the working branch you synchronized from VS Code to your GitHub fork has recent changes. Select **Compare & pull request**. branch has recent changes.

   [![Screenshot of the Compare & pull request page.](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-create-pull-request.png)](https://learn.microsoft.com/en-us/defender-office-365/media/add-advanced-hunting-community-queries-create-pull-request.png#lightbox)
3. Follow the guidance provided in the pull request description and answer as appropriate.
4. If you need to make further changes, you can select **Create draft pull request** to indicate the pull request isn't ready to be reviewed and approved. However, you can usually select **Create pull request** to proceed.
5. Someone with the permissions to merge the pull request will review your changes. The reviewer might request additional changes to conform with the standards of the repository. You can use [Create Advanced Hunting queries in the working branch](#step-4-create-advanced-hunting-queries-in-the-working-branch-in-the-cloned-repository-on-your-local-computer) and [Synchronize the changes from your local computer to the fork in your GitHub account](#step-5-synchronize-the-changes-from-your-local-computer-to-the-fork-in-your-github-account) to make requested changes on your local computer and synchronize them back into your fork so they're included in the pull request.

## Related resources

For more information about contributing queries to the Azure Sentinel community, see the following resources:

- Azure Sentinel Community - [Getting Started guide](https://github.com/Azure/Azure-Sentinel/blob/master/GettingStarted.md).
- Query Template structure - [Query Style Guide](https://github.com/Azure/Azure-Sentinel/wiki/Query-Style-Guide).
