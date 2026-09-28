<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-data-table -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Tutorial: Creating a Data Table

Carefully [creating and formatting a table](https://support.office.com/en-us/article/create-and-format-tables-e81aa349-b006-4f8a-9806-5af9df0ac664?wt.mc_id=fsn_excel_tables_and_charts "Excel Help & Training") using streaming data allows you to purposefully structure the information for storage and analysis.

In this tutorial, you learn how to:

- Use [named ranges](https://support.office.com/en-us/article/Define-and-use-names-in-formulas-4D0F13AC-53B7-422E-AFD2-ABD7FF379C64 "Excel Help & Training") to refer to ranges of streaming data.
- Create a blank table on a separate Excel sheet.
- Use [structured references](https://support.office.com/en-us/article/Using-structured-references-with-Excel-tables-F5ED2452-2337-4F71-BED3-C8AE6D2B276E "Excel Help and Training") to fill table with streaming data values from Data In named ranges.

## Prerequisites

- Data Streamer Enabled
- Sensor data streaming into Data In page of Excel

## Define Named Ranges for Streaming Data

<iframe src="https://learn-video.azurefd.net/vod/player?id=c426b7af-f279-4150-bef4-bb228a5ce4fc" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Open the **Data In** worksheet in your workbook.
2. Select the full data range under **Historical Data**, including the headers found in row 7.
3. Go to **Formulas > Create from Selection**.
4. In the **Create Names from Selection** dialog box, designate the location that contains the labels by selecting the **Top row** checkbox.
5. Select **OK**.

![Define named ranged.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/create-data-table/define-named-ranges.png)

Excel names the cell ranges based on the channel labels. These can be adjusted later in **Formulas > Name Manager**.

## Create Blank Table

<iframe src="https://learn-video.azurefd.net/vod/player?id=d1f4a9a0-e528-474d-9c9f-a5fec1809c78" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. In a blank worksheet, select a cell and type **Time** to be your first column name.
2. Continuing one cell right, type the name of your first data column.
3. Repeat for all desired data channels from Data In.
4. With one header cell selected, go to **Insert > Table**.
5. Select from your **Time** header and drag to add the necessary number of data rows to match Data In. Alternatively, just replace the last number in the range selection to include all desired rows.
6. Check the box for **My table has headers**.
7. Select **OK**.

![Create table.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/create-data-table/create-table.png)

This worksheet now has a blank table, which can now be filled through formulas.

## Fill Table with Streaming Data Values

<iframe src="https://learn-video.azurefd.net/vod/player?id=05a6b74b-5070-4b46-9e3d-8c90c0325c70" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. In a cell outside of your table, note the rate in seconds of your streaming data. \[#Note\]Ex: if you have a 20 ms interval between data, remember that your rate is .02.
2. Name this cell as `DataRate`.
3. In a cell in the **Time** column, enter the formula `=(ROW()-ROW([#Headers])-1)*DataRate`. This gives you a consistent time interval for your data.
4. In the second column, enter the formula `=INDEX(CH1_,ROW()-ROW([#Headers]))`.
5. Repeat for all desired channels of named ranges, replacing **CH1\_** with the valid named ranges.

This table is now filled with streaming data.
