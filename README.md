Select * from Zepto_data;

select SUM(sales) from Zepto_data;

Sum of sales  = Select CAST(SUM(sales) / 1000000 AS decimal(10,2)) AS Total_Sales_million from Zepto_data;

Average sales = Select CAST(AVG(sales) AS decimal(10))  as averag_sales from Zepto_data;

Count number of items = Select COUNT(*) as no_of_items from Zepto_data

Sum of sales filter low fat  = Select CAST(SUM(sales) / 1000000 AS decimal(10,2)) AS Total_Sales_million from Zepto_data where;

Avg sales for 2022 = Select CAST(AVG(sales) AS decimal(10))  as averag_sales from Zepto_data where Outlet_Establishment_Year = 2022; 

Number of items for 2022 = Select COUNT(*) as no_of_items from Zepto_data where Outlet_Establishment_Year=2022

Average rating = select CAST(AVG(Rating) as decimal(10,2)) as average_rating  from Zepto_data;

Total sales by fat content = select item_Fat_Content,CAST(SUM(Sales) as decimal(10,2)) as total_sales from Zepto_data group by Item_Fat_Content order by total_sales

select item_Fat_Content,CAST(SUM(Sales) as decimal(10,2)) as total_sales,
						CAST(AVG(sales) AS decimal(10))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 
from Zepto_data group by Item_Fat_Content order by total_sales



Total sales by item count = 
select item_Fat_Content,CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 					
from Zepto_data
group by Item_Fat_Content order by total_sales_thousand


 Total item types by item content = select Item_Type,CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 					
from Zepto_data
group by Item_Type order by total_sales_thousand

select top 5 Item_Type,CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 					
from Zepto_data
group by Item_Type order by total_sales_thousand asc


Fat content by outlet for total sales = 
select  Item_Fat_Content,Outlet_Location_Type,
                        CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 					
from Zepto_data
group by Item_Fat_Content,Outlet_Location_Type order by total_sales_thousand asc


Total sales by outlet establishment = 
select Outlet_Establishment_Year,
                        CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 					
from Zepto_data
group by Outlet_Establishment_Year order by total_sales_thousand asc

Percentage sales by outlet size = 
select Outlet_Size,
                        CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST((sum(Sales) * 100.0 / SUM(sum(sales)) over ()) as decimal(10,2)) as sales_percentage
from Zepto_data
group by Outlet_Size order by total_sales_thousand asc


Sales by outlet location = Select Outlet_Location_Type,  CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand from Zepto_data group by Outlet_Location_Type


All metric by outlet type = 
Select Outlet_Type,     CONCAT(CAST(SUM(Sales)/1000 as decimal(10,2)),'K') as total_sales_thousand,
						CAST((sum(Sales) * 100.0 / SUM(sum(sales)) over ()) as decimal(10,2)) as sales_percentage,
						CAST(AVG(sales) AS decimal(10,1))  as averag_sales,
						COUNT(*) as no_of_item,
						CAST(AVG(Rating) as decimal(10,2)) as average_rating 
from Zepto_data
group by Outlet_Type order by total_sales_thousand asc<img width="736" height="1828" alt="image" src="https://github.com/user-attachments/assets/5c8add08-fc4d-498c-bcdb-6412e06c09c2" />
