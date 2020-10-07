Pre-requisite:

[template excel]
Template excel has to be named "実行サイクル確認_template.xlsx" and placed inside the project folder
Template excel for Reporting format CAN have multiple sheets, but CANNOT have any formula or content inside
	- if there are formula inside, all sheets and headers will be dropped, but only the sorted and filtered rows will be saved 
	- if there are content inside, sorted and filtered rows will be appeneded after the last row with any content

[Chrome Browser]
- UiPath Chrome extension enabled
- Chrome browser logged in with an account with valid privileges if will download target google spreadsheets [RPA Service Management \ Process sheet] as input file(s)

[Kibana - Open Distro ]
- Access authority to target Kibana Visualiz(s)

[Config.xlsx]
-Adjust Config.xlsx\Setting 's ChromeDLSetting should be set to "manual" or "default" according to Chrome browser's download setting 

** ManualInputFileFlag = YES -> the inputfile exists check confirms for only 1 manual input file (Config.xlsx\Setting sheet : ManualInputFilePath). 
  ** Simply placing multiple input files will not break the workflow, so long as the 1 manual input file check clears when the flag is YES
  ** BUT, the existance of all manually provided input files will NOT be checked other than the 1 listed on Config.xlsx\Setting sheet : ManualInputFilePath



Output : 
- Output folder contains 実行サイクル確認_0814-0820.xlsx file with the ####-#### being 6days before run date - run date in MMdd-MMdd format













##############################################_UPDATES INFO & DESCRIPTION_###############################################################################

v1 
 # from RPA Service Management Sheet - Process.xlsx, output 実行サイクル確認 excel with corresponding filter and column format to
[https://docs.google.com/spreadsheets/d/1Z5mj0gBR_rptEJiYKCWye9YIqY_ne-LuhaSCEzNzyZc/edit#gid=229463946] 

v2 
 # Master sheet of template excel file will also be included

v2.1
 # Kibana Query by date period in Config.xlsx & integrate to output template file
 # default chrome browser download setting & manual chrome browser download setting enabled

v2.2
 # filters the downloaded RPA Service Management \ Process sheet by keeping only the rows with 
	column "status" = go-live 
		AND 
	column "business cycle" = one of
	{"< 15 Minutes" | "< 30 Minutes" | "< 1 Hour" | "< 1 Day" | "< 1 Week" | "< 1 Month" | "< 3 Month"}

v2.3
 # minor clean up 


v2.4
 # add "[sheetName]_ID" column to each one of Kibana Query exported reports 
 # add "実行サイクル確認表_ID" column to 実行サイクル確認 excel's 実行サイクル確認表 sheet 

--> add mapping by inserting ID column to template + 1wk + 1mo + 3mo
---> filter template by 1wk as 1wkconditionDT = join by 1wk = if exist = OK, else = error --> build new dt1wkIssue : -> add each row of dt1wkIssue to TEMPLATE column
---> filter template by 1mo as 1moconditionDT = join by 1mo = if exist = OK, else = error --> build new dt1moIssue : -> add each row of dt1moIssue to TEMPLATE column
---> filter template by 1mo as 3moconditionDT = join by 3mo = if exist = OK, else = error --> build new dt3moIssue : -> add each row of dt3moIssue to TEMPLATE column

v2.5
 # insert excel function to check and flag based on condition by referencing queried Kibana output 

v2.5.5
 # Kibana login with OC Asset is now able
 # Kibana query by in_int32QueryPeriodInDays as negative number case : query period by 1 day off bug fixed 
________________________________________________________________________________



body	sthsthsths
	++ enable taking diff input file 
	++enable potentially diff template columns, et c 
	
	
	
	
	make the email body to HTML ?? 
	seek to dev inputfile download + clean DL folder + inputfile folder & move. 
