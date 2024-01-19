SSIS: Loop without stage table in DB; load Excel data to Memory as variables for next operations

Steps: 
1. Setup file folders in your local machine. Here is 'C:\FILES\'
2. Create a simple excel file with User data "C:\FILES\Sources.xlsx", add three rows of data in 'User' sheet, here input: messi, ford, Tesla. 
3. Create a simple flat file C:\FILES\File.txt. 
4. Create SSIS package using the provided code with minor changes, OR, 
   create from scratch: 
	1) Create variables and assign to connect string of the connection managers, here is FlatFile_Destination
	2) Execute SQL task with query 'SELECT * FROM [User$A1:A4]', Resultset as 'Full result set'; third tab 'Result set': Result name 0 with object variable; 
	3) For Each loop: third tab 'Variable Mapping', assign object variables to user variables 'User::UserID' with 0 index
3. Run it and create three files renamed with three rows of data in Excel. 

Note: 
1. Similar following operations like 'Execute SQL Task':running stored proc using data from excel as variables; script task; Data flow task ...
2. If flat file as data source, need first ETL to excel file using DATA FLOW TASK. 
3. Pros: Provide a flexible approach: avoid stage table in DB to store data from excel; avoid cursor in SQL query; easy to debug; Cons: small amount of input data as variable

TESTED SUCESSFULLY in VS2017 Community Version

