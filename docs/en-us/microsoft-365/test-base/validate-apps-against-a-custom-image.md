<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/validate-apps-against-a-custom-image?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-09-14 -->

# Validate apps against a custom image

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

Note

This guide will show you how to onboard your own Windows image to Test Base as a baseline for security update or in-place upgrade validation.

## Custom Image

Many enterprises' IT departments have customized Windows builds which contain their tier 0 applications, configurations, and settings. Those images are commonly used for classic image-based deployment for new PCs or Windows updates. Test Base supports IT Pros, allowing them to share their custom image directly as a baseline to transfer the validation process to the cloud testing solution where the latest Windows updates can be deployed to their own image just as how they validate in their own environment to gain additional app confidence for monthly Windows updates or major Windows upgrade \(e.g. Windows 11 deployment pre-validation\). To set up your own image-based tests, please follow below guidance:

- [Prerequisites](#prerequisites)
- [Upload an image as baseline](#uploadanimageasbaseline)
- [Create an in-place upgrade test using a custom image as the baseline](#createinplaceupgrade)
- [Create a security update test using a custom image as the baseline](#createsecurityupgrade)

## Prerequisites

Users need to prepare their own images from working environments \(e.g. export from Configure Manager or take snapshots from Hyper-V\). Please follow below instructions to ensure the image is prepared in VHD format and compatible for Test Base usage. [How to prepare a Windows VHD for Test Base](https://learn.microsoft.com/en-us/microsoft-365/test-base/prepare-testbase-vhd-file?view=o365-worldwide)

## Upload an image as baseline

Users can upload images exported from their working environments to use as baseline for validation.

##### Step 1: Upload your VHD file

1. Visit the 'New image' tab from the navigation bar on the left. Click on the 'Upload VHD' link to direct to the VHD upload page.  [![Screenshot of `New image` page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_1.png?view=o365-worldwide#lightbox)
2. Click the "Select a VHD file to upload" button.  [![Screenshot of the `Select a VHD file to upload` button.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_2.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_2.png?view=o365-worldwide#lightbox)
3. Follow the instructions from the popup to select your VHD image file from local. Once selected, click 'Download' link to generate PowerShell script which would help upload the file from your local path via PowerShell.  [![Screenshot of the popup.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_3.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_3.png?view=o365-worldwide#lightbox)
4. Launch the PowerShell script from command line and provide the file path of the selected VHD to continue with the upload.
5. Once uploaded, refreshing the 'Upload VHD to storage blob' page will display your file in Validation/Ready mode.  [![Screenshot of refreshing the 'Upload VHD to storage blob' page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_4.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_4.png?view=o365-worldwide#lightbox)

##### Step 2: Create image from uploaded VHD

1. Visit the 'New image' tab under the left navigation bar
2. For the VHD section under 'Image source', select your uploaded VHD from the dropdown and make sure all the basic info for the image is correctly configured before publishing  [![Screenshot of the VHD section.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_5.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_5.png?view=o365-worldwide#lightbox)
3. Image creation might take a while to complete. Please stay on the resource deployment page until the creation process finishes.  [![Screenshot of the resource deployment page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_6.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_6.png?view=o365-worldwide#lightbox)
4. Access the 'Manage image' tab under the navigation bar. The new image should be under the 'Validation in progress' status with other existing images shown as below.  [![Screenshot of the page of `Manage image`.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_7.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_7.png?view=o365-worldwide#lightbox)

Note

The uploaded VHD files will be automatically deleted in 14 days in accordance to Microsoft's data retention policy. You may upload up to 10 custom images due to storage limitations.

## Create an in-place upgrade test using a custom image as the baseline

Users can create an in-place upgrade test by choosing an existing custom image as their baseline, allowing the validation to be based on their existing OS settings and configuration.

##### Step 1: Define custom image as the baseline from the 'Edit package' tab

1. Either create a new package or open an existing package to edit
2. Choose 'Flow driven' as in the 'Configure test' step and make the corresponding script changes in the 'Edit package' step.
3. Continue to the 'Test matrix' step and choose the target custom image from the dropdown list  [![Screenshot of the target custom image dropdown.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_8.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_8.png?view=o365-worldwide#lightbox)
4. Toggle on 'Pre-install security update release on baseline OS' if you would like the target security update installed before the base image gets upgraded. Otherwise, the latest available security update will be installed after the base image gets upgraded to the target OS version.  [![Screenshot of the page of test matrix.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_9.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_9.png?view=o365-worldwide#lightbox)
5. Review and publish the package once you have confirmed the Test matrix is properly configured with your desired custom image selected.  [![Screenshot of the `review and publish` page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_10.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_10.png?view=o365-worldwide#lightbox)

##### Step 2: Review the test result once your package has completed execution.

1. Under the navigation, click on the 'In-place upgrade results' tab and search for the package you created with your custom image as the baseline OS. The test results should be displayed for review.  [![Screenshot of the page of `In-place upgrade results`.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_11.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_11.png?view=o365-worldwide#lightbox)
2. Click the 'See details' link to view the package test results with your custom image as a baseline. There should be a 'Custom Image' tag next to your OS Product at the top to indicate your custom image was used as the baseline.  [![Screenshot of the page of test details.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_12.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_12.png?view=o365-worldwide#lightbox)

## Create a security update test using a custom image as the baseline

Users can create a security update test by selecting the desired custom image as the baseline from existing custom images to validation against their existing settings and configuration.

##### Step 1: Define the custom image as the baseline from the Edit package tab

1. Create a new package or open an existing package to edit
2. Choose 'Out of Box' or 'Functional' in the 'Configure test' step and make corresponding script changes in the 'Edit package' step.
3. Navigate to the 'Test matrix step', choose 'Security update' as the test type, and select the target custom image from the dropdown list of 'OS versions to test'  [![Screenshot of choose 'Security update'.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_13.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_13.png?view=o365-worldwide#lightbox)
4. Review and publish the package once you have confirmed the Test matrix is properly configured with your desired custom image selected.  [![Screenshot of the properly configured `review and publish` page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_14.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_14.png?view=o365-worldwide#lightbox)

##### Step 2: Review the test results once the package has completed execution

1. Under the left navigation bar, click on the 'Security update results' tab and search for the package you created with your custom image as the baseline OS. The test results should be displayed for review.  [![Screenshot of the page of `Security update results`.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_15.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_15.png?view=o365-worldwide#lightbox)
2. Click the 'See details' link to view the package test results with your custom image as a baseline.  [![Screenshot of the page of view the package test results.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_16.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/validate_apps_against_a_custom_image_16.png?view=o365-worldwide#lightbox)
