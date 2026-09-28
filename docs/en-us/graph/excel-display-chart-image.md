<!-- Source: https://learn.microsoft.com/en-us/graph/excel-display-chart-image -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Display a chart image in Excel

When you perform a [GET operation to retrieve a chart image](https://learn.microsoft.com/en-us/graph/api/chart-image), the Excel API in Microsoft Graph returns the image as a base-64 string. You can display the base-64 string inside an HTML image tag:

```html
 <img src="data:image/png;base64,{base-64 chart image string}/>
```

For default behavior, use `Image(width=0,height=0,fittingMode='fit')`.

Following is an example of a chart image returned with the default parameters.

![Excel chart image with default height and width.](https://cdn.graph.office.net/prod/GraphDocuments/en-us/concepts/images/GetChart-default.png)

If you want to customize the display of the image, specify a height, width, and a fitting mode. Here is what the same chart image looks like if you retrieve it with these parameters: `Image(width=500,height=500,fittingMode='Fill')`.

## Related content

- [Manage sessions in Excel with Microsoft Graph](https://learn.microsoft.com/en-us/graph/excel-manage-sessions)
- [Write to an Excel workbook using Microsoft Graph](https://learn.microsoft.com/en-us/graph/excel-write-to-workbook)
- [Use workbook functions in Excel with Microsoft Graph](https://learn.microsoft.com/en-us/graph/excel-use-functions)
- [Update a range’s format in Excel with Microsoft Graph](https://learn.microsoft.com/en-us/graph/excel-update-range-format)
- [Use the Excel REST API](https://learn.microsoft.com/en-us/graph/api/resources/excel)
