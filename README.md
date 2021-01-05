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
   ![SSIS_DataFlow.png](https://github.com/mazhur7/Data_Preprocessing/blob/master/SSIS_DataFlow.png)
Uplouding all data in the  Database tible:
image


* SQL proc :

```
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
```
INSERT INTO TABLE :
```
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
  
--EXCLUSIONS:
    WHERE ISNUMERIC([2015]) = 1
  or [2015] = ''
  
 -- (1049998 rows affected) 
 ```
ADDITIONAL EXCLUSIONS:
  The company was founded in the 1950s.  this means that anything befor 1950 and after 2016 can't be true.  Let's check that
  ```
  delete FROM [buisness_analysis].[dbo].[WRK_VehicleService_20210104]
  WHERE [CustomerSince] < '1950-01-01'
  or [CustomerSince] > '2017-01-01' --(1 row affected)
  ```
  
  CHECK DUPLICATES of Customers ID:
  ```
  select [CustomerID], count(*) 
  from [WRK_VehicleService_20210104]
  GROUP BY [CustomerID]
  HAVING COUNT(*)>1

  ```
  
  --additional checks
  ```
SELECT AVG([2016E]) AS ' avg2016', AVG([2014]) AS '2014', AVG([2015]) AS '2015' FROM [dbo].[WRK_VehicleService_20210104]
SELECT MAX([2016E]) AS ' max2016', MAX([2014]) AS '2014', MAX([2015]) AS '2015' FROM [dbo].[WRK_VehicleService_20210104]
SELECT MIN([2016E]) AS 'min 2016', MIN([2014]) AS '2014', MIN([2015]) AS '2015' FROM [dbo].[WRK_VehicleService_20210104]
SELECT sum([2016E]) AS ' sum2016', sum([2014]) AS '2014', sum([2015]) AS '2015' FROM [dbo].[WRK_VehicleService_20210104]
```
We found that in max2014 '2000' doesn't seem to be true value
```
SELECT * FROM [dbo].[WRK_VehicleService_20210104]
where [2014] = 20000
or [2014] > 800
```
check the benchmark amount of annual income that we knew.
```
SELECT sum([2016E]) AS ' sum2016', sum([2014]) AS '2014', sum([2015]) AS '2015' FROM [dbo].[WRK_VehicleService_20210104]

SELECT count(*) FROM [buisness_analysis].[dbo].[RAW_VehicleService_20210104]
*/
```
  
