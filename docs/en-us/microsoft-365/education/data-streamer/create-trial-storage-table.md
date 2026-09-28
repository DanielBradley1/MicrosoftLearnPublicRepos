<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-trial-storage-table -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Tutorial: Create a Trial Storage Table

In this tutorial, you learn how to:

- Name your data table
- Add additional structured columns for trial storage
- Add objects for macro button interactions

## Prerequisites

- Data Streamer Enabled
- Sensor data streaming into a structured table in Excel

## Name the Data Table

\[!VIDEO https://learn-video.azurefd.net/vod/player?id=c426b7af-f279-4150-bef4-bb228a5ce4fc\]

1. Select a cell in your table.
2. Go to **Table Design > Properties** and select the box under **Table Name**.
3. Rename your table as desired.

Your table now has a set name that can be verified and referenced by macros.

## Add Additional Structured Columns for Trial Storage

<iframe src="https://learn-video.azurefd.net/vod/player?id=ba1b1625-ed02-4df2-92d3-4c8c91d7c6f5" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Select the first cell to the right of the table headers.
2. Type in a desired name for your first trial column of your first sensor.
3. Repeat, still just for all other desired sensors desired to be stored per trial.

   - Keep the naming convention repeatable and consistent. Ex: *CH1\_T1*, *CH2\_T1*, etc.

4. Repeat the same naming convention for all additional trials, each for storing the same sensors' data.

   - Ex: *CH1\_T1*, *CH2\_T1*, *CH1\_T2*, *CH2\_T2*, etc.

This table now has blank columns for saving and storing channels of data.

## Add Objects for Macro Button Interactions

<iframe src="https://learn-video.azurefd.net/vod/player?id=412d2e93-034c-445f-a6dc-77aa99c442dd" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Go to **Insert > Shapes**
2. Select a shape from this menu, such as a **Rectangle**
3. Name this shape to end with a consistent integer, such as *SaveTrial1*

   - This allows macros to look at the name object in order to understand to what trial should the macro refer.

4. Select this object again and type this shapes' name, to make the name easier to see later.
5. Repeat steps 2-4 for all additional trials.

Your sheet now has buttons that can later have macros attached to them, using their name to change the interaction.
