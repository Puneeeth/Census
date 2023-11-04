1) Identify number of Rows?

select count(*) From census.eda_1
select count(*) From census.eda_2

2) Analysing specific data by State/City

select * from census.eda_1
where State="Karnataka" 

select * from census.eda_2
where District IN ("Bangalore","Agra")

select * from census.eda_1
where state like "%A"

select * from census.eda_1
where state like "%na%"

3) Analysing Population, Sex Ratio, Growth and Literacy

select sum(Population) AS Total_Population from census.eda_2

SELECT  AVG(growth) * 100 AS average_growth FROM census.eda_1

SELECT  AVG(sex_ratio) * 100 AS average_sex_ratio FROM census.eda_1

SELECT  AVG(literacy) * 100 AS average_literacy FROM census.eda_1

SELECT round (AVG(literacy), 0) * 100 AS average_literacy FROM census.eda_1

4) Top 10 States by

a.Toatl Population
select sum(Population)  AS Total_Population, state from census.eda_2
group by state
order by state asc
limit 11

b.Average Literacy
select avg(Literacy) * 100 AS average_literacy, state from census.eda_1
group by state
order by state asc
limit 10

c.Average Growth
select avg(growth) * 100 AS average_growth, state from census.eda_1
group by state
order by state asc
limit 10

d.Average Sex Ratio
select avg(sex_ratio) * 100 AS average_sex_ratio, state from census.eda_1
group by state
order by state asc
limit 10

5) Average sex ratio in states above 90000
select avg(sex_ratio) * 100 AS average_sex_ratio, state from census.eda_1
group by state
having average_sex_ratio > 90000

6)Find the states with highest Average Literacy
select state, avg(literacy) * 100 AS avg_literacy  eda_1
GROUP BY state
HAVING avg(literacy) > 90
ORDER BY avg_literacy DESC 

7)Top 10 States by Literacy Ratio and Population 
select literacy, population, census.eda_2.district from census.eda_1
Inner join census.eda_2 on census.eda_1.District = census.eda_2.district
order by district desc
limit 10
