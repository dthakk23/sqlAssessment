# SQL Challenge

The database contains two tables, store_revenue and marketing_data.  Refer to the two CSV
files, store_revenue and marketing_data to understand how these tables have been created.

store_revenue contains revenue by date, brand ID, and location:

 >  create table store_revenue (
 >     id int not null primary key auto_increment,
 >    date datetime,
 >    brand_id int,
 >    store_location varchar(250),
 >    revenue float  
 >  );

marketing_data contains ad impression and click data by date and location:

> create table marketing_data (
>  id int not null primary key auto_increment,
>  date datetime,
>  geo varchar(2),
>  impressions float,
>  clicks float
> );

### Please provide a SQL statement under each question.

* Question #0 (Already done for you as an example)
 Select the first 2 rows from the marketing data
​
>  select *
>  from marketing_data
> limit 2;
​
*  Question #1
 Generate a query to get the sum of the clicks of the marketing data

​>​SELECT Sum(Clicks) AS Sum_OF_Clicks
>FROM marketing_data;

*  Question #2
 Generate a query to gather the sum of revenue by geo from the store_revenue table

 >SELECT store_location, Sum(Revenue) AS Sum_OF_Revenue
 >FROM Store_Revenue
 >GROUP BY store_location;


*  Question #3
 Merge these two datasets so we can see impressions, clicks, and revenue together by date
and geo.
 Please ensure all records from each table are accounted for.
​
>SELECT marketing_data.impressions, marketing_data.clicks,marketing_data.geo, Store_revenue.date, Store_revenue.revenue
>FROM marketing_data Right  Outer Join  Store_Revenue
>ON marketing_data.date= Store_Revenue.date
>Group by marketing_data.geo,Store_Revenue.date,marketing_data.impressions, marketing_data.clicks,Store_revenue.revenue
;
* Question #4
 In your opinion, what is the most efficient store and why?

-For this question I would consider 2 factors. The first being how many impressions where being converted to clicks. That is what matters I believe when considering such data. For that I found that State: MN has the greatest conversion rates. The code used for the following is:
>Select Sum(Clicks) as CL, Sum(Impressions) as IMP, Sum(Clicks)/Sum(Impressions)*100 as Success , geo from marketing_data
>Group by geo;

-Secondly, I would consider the total revenue. The state CA had the highest revenue.

-It depends on the business needs and goal which we are trying to reach. Based on that we can either select CA or MN.

​
* Question #5 (Challenge)
 Generate a query to rank in order the top 10 revenue producing states

>SELECT store_location, revenue
>FROM store_revenue
>Order By revenue desc limit 10;
​