<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/review?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Step 6: Review your selections and create your package.

1. On this tab, the service displays your test details and runs a quick completeness check.

   A **Validation passed** or **Validation failed** message shows whether you can proceed to next steps or not.
2. Review your test details and if satisfied, select the **Create** button.

   [![View validation.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validation.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validation.png?view=o365-worldwide#lightbox)
3. This onboards your package to the Test Base environment. If your package is successfully created, an automated test that verifies whether your package can be successfully executed on Azure will be triggered.

   ![Successful result.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/successful.png?view=o365-worldwide)

   Note

   You'll get a notification from the Azure portal to notify you on the success or failure of the package verification.

   Note that the process can take up to 24 hours, so it's likely your webpage will timeout if you aren't active on it and hence, the notification won't inform you of the completion of this on-demand run.

   - Peradventure this happens, you can view the status of your package on the **Manage packages** tab.

     [![Image for managing packages.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/managepackages.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/managepackages.png?view=o365-worldwide#lightbox)
   - For successful tests, their results can be seen via the **Test Summary**, \*\*Security Updates Results, and **Feature Updates Results** pages at scheduled intervals, often starting a few days after your upload.
   - While failed tests, require you to upload a new package.

     You can download the **test logs** for further analysis from the **Security update results** and **Feature updates results** pages.
   - If you experience repeated test failures, please reach out to testbasepreview@microsoft.com with details of your error.

## Next steps

Discover our Content Guidelines via the link below.

[Next step](https://learn.microsoft.com/en-us/microsoft-365/test-base/contentguideline?view=o365-worldwide)
