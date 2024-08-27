# Sipp Beverages Financial Analysis Dashboard

<p align="center">
  <img src="https://github.com/user-attachments/assets/7300c650-c92b-4915-a0a2-51f3ed0b96ef" width="800">
</p>
<p align="center">
  <em>Dashboard showing performance from Jul 2019 - Jun 2020</em><br>
</p>


## Project Overview
The Sipp Beverages Financial Analysis Dashboard offers a comprehensive look at the performance of Sipp Beverages, a fictitious company operating in the Fast Moving Consumer Goods (FMCG) industry. This dashboard is designed to provide actionable insights into key financial metrics, enabling data-driven decision-making. Key features include visualizations of monthly net sales and gross profit, purchase volume by bottle size, and client type. The dashboard also incorporates interactive filters for dynamic analysis across different time periods and brands. Click on [Financial Analysis Dashboard](https://public.tableau.com/app/profile/justice.paintsil/viz/FinancialDashboard-SippBeveragesLtd_/SippReport#1) to interact with the dashboard on Tableau Public.

At the top of the dashboard, four key performance indicators (KPIs) are prominently displayed:

* **Total Revenue:** The total amount of money earned from sales before any deductions.
* **Average Discount %:** The average discount provided to clients during purchases.
* **Average Distribution Cost %:** The relative cost associated with delivering products to clients.
* **COGS % of Gross Sales:** The percentage of revenue spent on producing the goods sold.

One of the standout features of this dashboard is the interactive filters, which transform static reports into dynamic, actionable insights. The time filter, for instance, allows users to explore data across different periods—whether by month, quarter, or year—enabling a thorough analysis of the company’s progress. Additionally, a brand filter provides the ability to drill down into the performance of individual brands within the Sipp Beverages portfolio, delivering critical insights into brand-specific growth and profitability.

## Building the Dashboard
The data for this dashboard was sourced from a CSV file containing financial information, typically extracted from an ERP system like SAP or Oracle. After loading the dataset into Tableau, I analyzed its structure and identified it as time series data, complete with details about Sipp Beverages’ clients and categorization by client type. The dataset also included essential financial metrics such as Volume, Gross Sales, Discounts, Net Sales, Cost of Goods Sold (COGS), Distribution, and Warehousing.

Each element of the dashboard—charts and KPIs—was created on separate worksheets in Tableau. Once all the components were built, I brought them together in the final dashboard, where I added filters to make the dashboard dynamic and interactive. The key worksheets created were Net Sales and GP %, Volume by Size, and Volume by Client Type, in addition to the four KPI worksheets mentioned earlier. The final dashboard was aptly named "Sipp Report."

### Visualizations

#### Custom Color Palette
Before constructing the charts, I created a custom color palette, named ‘Violet Blu Peach,’ to align with Sipp Beverages’ corporate branding. This involved modifying the ‘Preferences.tps’ file in My Tableau Repository by inserting the appropriate hex color codes using a text editor. The custom palette then became available within Tableau for all visual elements.

#### Net Sales and GP % (Combination Chart)
This combination chart features a bar chart for monthly net sales alongside a line chart for gross profit margins. The net sales data indicates the pace of business growth, while the gross profit margin provides insights into profitability. Although both charts share the same time axis, each has a distinct y-axis to represent different scales—net sales in currency and gross profit as a percentage. Below are the technical steps to create the [Net Sales and GP % combo chart](KPIs%20and%20Charts%20Worksheets/Net%20Sales%20and%20GP%20%20Worksheet.png):

* Drag Year and Month from the Dimensions panel to the Columns shelf.
* Drag Net Sales from the Measures panel to the Rows shelf.
* Right-click on both Year and Month and select Discrete to convert them into discrete fields.
* Click on Analysis and select Create Calculated Field.
* Name the field GP % and enter the formula: 
  * `SUM([Net Sales] + [Cost of Goods Sold]) / SUM([Net Sales])`. Click OK.
  * *Note: The formula sums Net Sales and Cost of Goods Sold since COGS is represented as a negative value in the dataset.* [Click to see the image of the formula in Tableau](Dashboard%20Images/GP%20%20Calculation.png).
* Drag GP % from the Measures panel to the Rows shelf. This creates a second bar chart.
* Click on the GP % chart under the Marks card and change the mark type to Line from the drop-down menu.
* Right-click on the y-axis of the GP % chart and select Dual Axis to overlay the charts.
* If the bars change to dots, click on SUM(Net Sales) under the Marks card and set the mark type back to Bar.
* Right-click on the secondary y-axis (for GP %) and select Format.
* Under the Numbers drop-down, choose Percentage and set the Decimal Places to 2. Align the text to the center.
* Double-click the chart title and rename it to Net Sales and GP %. Format the title in bold.
* Click on Color under the Marks card for the GP % line and select the second markers option to make the data points stand out.
* While still under Color, click Edit Colors.
* Select Violet Blu Peach from the drop-down list under Select Color Palette.
* Assign the dark purple color to GP % and a blue color to Net Sales. Click Apply and then OK to confirm.

#### Volume by Size (Horizontal Bar Chart)
This chart visualizes the purchase volumes across different package sizes for Sipp Beverages’ products, making it easy to compare the performance of various sizes. Follow the steps below to create the [Volume by Size horizontal bar chart](KPIs%20and%20Charts%20Worksheets/Volume%20by%20Size%20Worksheet.png):

* Setup Axes: Drag Volume from the Measures panel to the Columns shelf.
* Drag Size from the Dimensions panel to the Rows shelf.
* Adjust the order of the bars to reflect the bottle sizes by simply dragging and dropping them into the desired sequence.
* Double-click the chart title and rename it to Volume by Size. Format the title as bold for emphasis.
* To color each bar uniquely, right-click on a bar and select Group. Repeat this for all bars to create separate groups.
* Assign different shades of blue and purple to the grouped bars to visually distinguish the volume sizes, following the approach from the previous steps.
* Drag Gross Sales from Measures onto Label. Right-click on any of the data labels and choose Format. Click the drop-down arrow beside Numbers, select Currency, and choose Million.

#### Volume by Client Type (Horizontal Bar Chart)
This chart categorizes purchase volumes by client type, including Big-box, Discounters, Grocery, and Supermarkets, offering a clear view of client distribution patterns. To create the [Volume by Client Type horizontal bar chart](KPIs%20and%20Charts%20Worksheets/Volume%20by%20Client%20Type%20Worksheet.png) follow the steps below:

* Drag Volume from the Measures panel to the Columns shelf.
* Drag Client Type from the Dimensions panel to the Rows shelf.
* Double-click the chart title and rename it to Volume by Client Type. Make the title bold for emphasis.
* Right-click on each bar and select Group to organize them by client type.
* Use different shades of blue and purple to color the grouped bars, similar to the method used in the previous step, to visually distinguish the client types.
* Drag Gross Sales from Measures onto Label. Right-click on any of the data labels and choose Format. Click the drop-down arrow beside Numbers, select Currency, and choose Million.

### Key Performance Indicators (KPIs)

#### Steps to Calculate and Format KPIs:

#### Total Revenue
This metric is calculated by summing all values in the Gross Sales field.

1.	Go to Analysis and select Create Calculated Field.
2.	Enter **Total Revenue** as the name of the calculated field and input the formula:
    * `SUM([Gross Sales])`. Click OK.
4.	Double-click the new measure ‘Total Revenue’.
5.	Right-click on the measure in the Rows shelf and select Discrete to convert it from Continuous to Discrete.
6.	Right-click on the number in the table and choose Format. Click the drop-down arrow beside Numbers, select Currency, and choose Million. Retain the default Decimal Places of 2. Align the number and text to the center and make the text bold.

#### Average Discount %
This value is calculated by dividing the total discounts by the sum of gross sales.

1.	Go to Analysis and select Create Calculated Field.
2.	Enter **Average Discount %** as the name of the calculated field and input the formula:
    * `SUM([Discount]) / SUM(-[Gross Sales])`. Click OK.
  	* *Note: The minus sign is used because the Discount variable is represented with negative values in the data.*
4.	Double-click the new measure **Average Discount %**.
5.	Right-click on the measure in the Rows shelf and select Discrete to convert it from Continuous to Discrete.
6.	Right-click on the number in the table and choose Format. Click the drop-down arrow beside Numbers and select Percentage. Retain the default Decimal Places of 2. Align the number and text to the center and make the text bold.

#### Average Distribution Cost % 
This KPI is computed by dividing the sum of Distribution by the sum of Net Sales.

1.	Go to Analysis and select Create Calculated Field.
2.	Enter **Average Distribution Cost %** as the name of the calculated field and input the formula:
    * `SUM([Distribution]) / SUM(-[Net Sales])`. Click OK.
  	* *Note: The minus sign is used because the Net Sales variable is represented with negative values in the data.*
4.	Double-click the new measure **Average Distribution Cost %**.
5.	Follow steps 4 and 5 as outlined above to format the value and text.

#### COGS % of Gross Sales
This metric is calculated by dividing the sum of COGS by the sum of Gross Sales.

1.	Go to Analysis and select Create Calculated Field.
2.	Enter **COGS % of Gross Sales** as the name of the calculated field and input the formula:
    * `SUM([Cost of Goods Sold]) / SUM(-[Gross Sales])`. Click OK.
  	* *Note: The minus sign is used because the Cost of Goods Sold variable is represented with negative values in the data.*
4.	Double-click the new measure **COGS % of Gross Sales**.
5.	Follow steps 4 and 5 as outlined above to format the value and text.

## Dashboard Design
To create the dashboard, I set the dimensions to a minimum of 1080x720 pixels and a maximum of 1400x1000 pixels. I used the Tiled layout to organize and position the various elements neatly. The KPIs were placed at the top of the dashboard, followed by the combination chart (Net Sales and GP %) and the two bar charts (Volume by Size and Volume by Client Type) below. The company logo was added to the top left corner, with the dashboard title prominently displayed next to it.

#### Interactive Filters
Filters are critical to making this dashboard truly interactive. I added two main filters:

* **Brand Filter:** This filter allows users to isolate and examine data related to specific brands within Sipp Beverages. It is essential for understanding individual brand performance and identifying growth opportunities or underperforming areas.
* **Date Filter:** To enable time-based analysis, I created a [Start Date](Parameters%20(Start%20and%20End%20Dates)/Start%20Date%20Parameter.png) and [End Date](Parameters%20(Start%20and%20End%20Dates)/End%20Date%20Parameter.png) parameters. These parameters allow users to adjust the time frame for the data, making it possible to review performance over any chosen period, whether monthly, quarterly, or yearly.

Both filters were customized for ease of use. The Brand filter was connected to all worksheets, and I ensured that the Date filter was set up to work across the entire dashboard. This seamless integration of filters ensures that users can dynamically explore the data and gain insights tailored to their specific needs.

## Dashboard Review and Interpretation
The dashboard offers a multifaceted view of Sipp Beverages’ financial data. Users can track net sales and gross profit margins to assess overall business growth and profitability. Additionally, the breakdown of sales by client type and product size provides valuable insights into market trends and client preferences.

With the time filter, users can review the company’s performance over various periods, be it monthly, quarterly, or annually. The brand filter further enhances the dashboard’s utility by allowing a focused analysis of individual brands, which is crucial for making informed strategic decisions.

By adjusting these filters, users can address key business questions such as:

* Which brands are performing well?
* Are any brands underperforming or losing money?
* How do sales trends vary across different periods?

For example, if a report on the company’s performance over the last 12 months is needed, users can simply adjust the start and end dates to view the relevant data. 

* **Yearly Performance Review:** Adjust the start and end dates to generate a report on the company’s performance over the last 12 months.
<p align="center">
  <img src="https://github.com/user-attachments/assets/0b046e4d-4f0c-4259-88a3-f3c855198550" width="800">
</p>
<p align="center">
  <em>Dashboard showing performance from Jan-Dec 2020</em><br>
</p>


Alternatively, the data can be filtered to analyze specific quarters, such as Q1-2020, to assess whether sales targets were met.

* **Quarterly Analysis:** Narrow the time frame to a specific quarter, such as Q1-2020, to determine if sales quotas were met.
<p align="center">
  <img src="https://github.com/user-attachments/assets/08b5cbef-09bf-46f9-8ecd-dc46365cde9d" width="800">
</p>
<p align="center">
  <em>Dashboard displaying performance in Q1-2020</em><br>
</p>


Moreover, the brand filter can be used to monitor newly created brands, ensuring that their integration into the company portfolio is on track. The ability to zoom in on specific aspects of the company’s performance ensures that management can make data-driven decisions, adapt strategies, and refine business goals over time.

## Conclusion
The Sipp Beverages [Financial Analysis Dashboard](https://public.tableau.com/app/profile/justice.paintsil/viz/FinancialDashboard-SippBeveragesLtd_/SippReport#1) is designed to provide clear, actionable insights into the company’s financial performance. By combining KPIs, dynamic visualizations, and interactive filters, this dashboard not only highlights key metrics but also supports strategic decision-making at both the brand and company levels. As business goals evolve, this dashboard can be adapted to reflect new priorities, ensuring it remains a valuable asset for ongoing financial analysis.
