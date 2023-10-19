# PowerBICookbook
Power BI Cookbook resources. There are 3 .pbix files in this repository.

# In CustomerNoFilterExample.pbix, I demonstrate how to create a report that can be used in a Factbox of a List page in Business Central and filters on the selected record on the List page.

The following are two date table examples: 

# In DateTable-Example1.pbix, the entire table creation is done in a single query/script. If you intend to copy the query to use in your .pbix, be sure to mark the table as a date table.

Calendar = 
VAR _calendar =
	CALENDAR (1/1/2011, 12/31/2030)
RETURN
	ADDCOLUMNS (
		_calendar,
		"Year", YEAR ( [Date] ),
		"MonthNumber", MONTH ( [Date] ),
		"Month", FORMAT ( [Date], "mmmm" ),
		"Quarter", "QTR" & FORMAT ( [Date], "Q" ),
		"QuarterNumber", FORMAT ( [Date], "Q" ),
		"MonthYearNumber", FORMAT([Date], "yy mm"),
		"Month Year", FORMAT([Date], "mmm yyyy")
)

# In DateTable-Example2.pbix, a simple table is created first, marked as a date table, followed by individually creating day, week, month, quarter and year, and finally arranged in a hierarchy. The periods in this example are better formatted.

Step 1: Create a New Table

DATETABLE = 
CALENDAR(DATE(2018,1,1), DATE(2030,12,31))

Step 2: Mark as Date Table

Step 3: Create new columns one by one

Day = FORMAT(DATETABLE[Date], "YYYY-MM-") & DAY(DATETABLE[Date])

Month = FORMAT(DATETABLE[Date], "YYYY-MM (MMM)")

Quarter = YEAR(DATETABLE[Date]) & "-Q" & FORMAT(DATETABLE[Date], "Q")

Week = YEAR(DATETABLE[Date]) & " WK " & WEEKNUM(DATETABLE[Date], 21)

Year = YEAR(DATETABLE[Date])

Step 4: Create Date Hierarchy

Click on Date and right-click to "Create Hierarchy"

Add D, W, M, Q, Y to hierarchy

