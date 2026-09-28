<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/visualize-streaming-data-in-excel -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Tutorial: Visualize Streaming Data in Excel

[Creating a chart](https://support.office.com/en-us/article/create-a-chart-from-start-to-finish-0baf399e-dd61-4e18-8a73-b3fd5d5680c2?ui=en-US&rs=en-US&ad=US "Excel Help & Training") from streaming data helps maximize the visual impact of your data for your audience. Learn below how to create dynamic charts from your streaming data.

In this tutorial, you learn how to:

- Visualize the current value for connected sensors
- Visualize values over time for connected sensors

## Prerequisites

- Data Streamer Enabled
- Sensor data streaming into Data In page of Excel

## Visualize the Current Value for Connected Sensors

<iframe src="https://learn-video.azurefd.net/vod/player?id=e86fda56-1fd9-4567-9d18-a3dd22bfbb17" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Go to the **Data In** worksheet in your workbook.
2. Select the current data for the channels you wish to visualize, as found in Row 5.
3. Select **Insert > Recommended Charts**.
4. Select a desired chart from either this recommended list or from the **All Charts** tab. By default, try a column chart.
5. Select **OK** to add the selected chart to your Excel sheet.
6. Select **Data Streamer > Stop Data** to halt streaming data, to allow axis edits.
7. Select the value axis and set the bounds for this axis.

![Visualize Current Values.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/visualize-streaming-data-in-excel/visualize-current-data.png)

Now, when **Data Streamer > Start Data** has been selected, this chart visualizes the latest sensor values.

## Visualize Values Over Time for Connected Sensors

<iframe src="https://learn-video.azurefd.net/vod/player?id=82f2c0ee-09ad-4923-85ab-ab7daf73c561" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Select the full range of historical data for the channels you wish to visualize.
2. Select **Insert > Recommended Charts**.
3. Go to **All Charts** and select a **Line** or **Scatter** chart for your visualization.
4. The selected chart should shows the same number of unique Series as selected Channels.
5. Select **OK** to add the selected chart to your Excel sheet.
6. Select **Data Streamer > Stop Data** to halt streaming data, to allow axis edits.
7. Select the value axis and set the bounds for this axis.

![Visualize Values Over Time.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/visualize-streaming-data-in-excel/visualize-values-over-time.png)

Now, when **Data Streamer > Start Data** has been selected, this chart visualizes the change in values over time for your sensors.
