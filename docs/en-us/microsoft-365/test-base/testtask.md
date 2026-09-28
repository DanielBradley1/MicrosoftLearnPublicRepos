<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/testtask?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2022-08-11 -->

# Step 4: The tasks tab

On the tasks tab, you're expected to provide the paths to your test scripts that are in the zip folder you uploaded under the binaries tab.

- **Out of Box Test Scripts:** Type in the relative paths to your install, launch, close and uninstall scripts. You also can select extra settings for the install script.
- **Functional Test Scripts:** Type in the relative path to each functional test script uploaded. Extra functional test scripts can be added using the `Add Script` button. You need a minimum of one \(1\) script and can add up to eight \(8\) functional test scripts.

  The scripts run in the sequence they're listed. A failure in a particular script stops subsequent scripts from executing. You also have the option of selecting extra settings for each script provided.

## Set script path

![Image of test task.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testtask.png?view=o365-worldwide)

Sample of how to provide the relative path on a folder structure is below:

***Zip\_file\_uploaded***

```
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- **ScriptX.ps1** would have. *ScriptX.ps1* as the relative path.
- **Script.ps1** would have *folder1/script.ps1* as the relative path.

## Next steps

View details of the Test Options tab in the next article

[Next step](https://learn.microsoft.com/en-us/microsoft-365/test-base/testoptions?view=o365-worldwide)
