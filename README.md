##  data pipline 
- [x] **Data Preprocessing** 
- [ ]  Data Analyses & Machine Learning
- [ ]  Data Visualisation 

![PreparationPhase.jpg](https://github.com/mazhur7/Data_Preprocessing/blob/master/PreparationPhase.jpg)
# Working with Data: The preparation Phase
- Example: We have the csv dataset  containing over a million rows.
      * Notepad++: chek the colomns determination. Since the rows are larger than the excel sheet, we divide the file into two .txt files 
      * Excele: Load data from txt files (SQL Query or or Import data tools. trancsofrm data views. Save as csv file
      * Notepad++: Put the data from two csv files in the final file(csv)
   * M Visual Studio SSIS 
   
Uplouding all data in the  Database tible:
image


* SQL proc :

'''
CREATE TABLE [WRK_VehicleService_20210104]
  (
  [RowNumber]		INT IDENTITY (1,1)
	  ,[CustomerID]	VARCHAR(50)
      ,[CustomerSince] date
      ,[Vehicle]	VARCHAR(500)
      ,[2014]		FLOAT
      ,[2015]		FLOAT
      ,[2016E]		FLOAT
  )
'''
INSERT INTO TABLE 
'''
INSERT INTO [buisness_analysis].[dbo].[WRK_VehicleService_20210104]
(    
      [CustomerID]
      ,[CustomerSince]
      ,[Vehicle]
      ,[2014]
      ,[2015]
      ,[2016E]
  )

SELECT 
      [CustomerID]
      ,[CustomerSince]
      ,[Vehicle]
      ,[2014]
      ,[2015]
      ,[2016E]
  FROM [buisness_analysis].[dbo].[RAW_VehicleService_20210104]
  
--EXCLUSIONS
    WHERE ISNUMERIC([2015]) = 1
  or [2015] = ''
  
 -- (1049998 rows affected) 
  '''
