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
​
* Question #5 (Challenge)
 Generate a query to rank in order the top 10 revenue producing states

>SELECT store_location, revenue
>FROM store_revenue
>Order By revenue desc limit 10;
​