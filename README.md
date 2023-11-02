# PowerBI
HotelRevenue Dashboread
******************************** Project****************************** 
        
  → Build a visual data story or dashboard using Power Bi to Present to your stakeholders.
              → Is our hotel revenue growing by year?
              → should we increase our parking lot size?
             → What trends can we see in the data ?

Data Analysis Project Pipeline
   → Build a Database 
   → Develop the SQL Query
   → Connect Power BI to the database
   → Visualize
   → Summarize Findings

Project [Database]
Tables
   → 2018
   →2019
   →2020
Union it will merge into 1 table

************************ 	Merging columns ***************************
with hotels as (
select * from dbo.['2018$']
union
select * from dbo.['2019$']
union
select * from dbo.['2020$']
)

select * from hotels

************************ SUM,  MUL***************************
   → Here, adding 2 columns
   → Multiplying  * another column 
   → Naming column as Revenue 
   And
  → Doing Grp by (it will get in one year how much revenue got )

CODE:- 
select 
arrival_date_year,
sum((stays_in_weekend_nights + stays_in_week_nights)*adr ) as revenue 
from hotels
group by arrival_date_year




************************ Adding one more column***************************
→ Here, there is two hotels so in which yr , in which hotel how much revenue need to check 
So 
Code ➖

select 
arrival_date_year,
hotel,
round(sum((stays_in_weekend_nights + stays_in_week_nights)*adr ),2) as revenue 
from hotels
group by arrival_date_year,hotel

→ that,hotel is hotel names
So it will give
Date yr       hotelName    Revenue

************************ need to merge different  column ***************************
→ Here, see hotels is new table with merging all 3 tables right
→ here there another table called market segment 
→ so in hotels also there is market segment column 
→ now this Another Table market segment NEED to merge in hotels Market segment column 

Code:- 
select * from hotels 
join dbo.market_segment$
on hotels.market_segment = market_segment$.market_segment




************************ Power BI***************************
         
        → First connect the sql server in power bi
        → with advanced option
        → adding query which did in sql 
        → when data is load 
        → Click on transform data it will open another desktop 
        → adding new column to AS Revenue 
        → writing the kind of query in power bi 
            [ adding weekend + week days * adr * discount ] this are column 
        → it will create new colum as Revenue and 
        → Close and Apply


