#Hotel_revenue_project using prostgreSQL with pgAdmin platform
--All data pulled from https://www.absentdata.com/hotel_revenue_historical_full/

--Query to collect data from all 3 years to generate total revenue by year
with hotels as (
select * from public."2018"
union
select * from public."2019"
union
select * from public."2020"
)
select
arrival_date_year as year,
sum((stays_in_weekend_nights+stays_in_week_nights)*adr) as revenue 
from hotels
group by arrival_date_year

