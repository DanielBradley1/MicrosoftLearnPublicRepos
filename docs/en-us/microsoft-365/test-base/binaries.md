<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/binaries?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2022-08-11 -->

# Step 3: Upload your binaries, dependencies, and scripts

On this tab, you'll upload a single zip package containing your binaries, dependencies and scripts used to run your test suite.

Note

The size of the zip package should be between a minimum of 10 MB and a maximum of 2 GB.

## Upload package zip file

![Upload your binaries.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/addbinaries.png?view=o365-worldwide)

- Uploaded dependencies can include test frameworks, scripting engines or data that will be accessed to run your application or test cases. For example, you can upload Selenium and a web driver installer to help run browser-based tests.
- It's best practice to ensure your script activities are kept modular that is.

  - The `Install` script only performs install operations.
  - The `Launch` script only launches the application.
  - The `Close` script only closes the application.
  - The optional `Uninstall` script only uninstalls the application.

**Currently, the portal only supports PowerShell scripts.**

## Next steps

Advance to the next article to go onto Step 4: **Set your Test Tasks**.

[Go back](https://learn.microsoft.com/en-us/microsoft-365/test-base/uploadapplication?view=o365-worldwide)

[Next step](https://learn.microsoft.com/en-us/microsoft-365/test-base/testtask?view=o365-worldwide)
