# World_Populations_Analysis

/*-- How many entries in the database are from Africa? */
Select count(*) from countries where continent ='Africa' ;

Query Results
count(*)
56


/*-- What was the total population of Oceania in 2005? */

select sum(population) as total_population from population_years join countries on 
countries.id = population_years.country_id
where  continent ='Oceania' and year ='2005'

Query Results
total_population
32.66417

/* -- What is the average population of countries in South America in 2003?*/

select round(avg(population),2) as average_population from population_years join countries on 
countries.id = population_years.country_id
where  continent ='South America' and year ='2003'

Query Results
average_population
25.89


/* -- What country had the smallest population in 2007? */

select population ,name  from population_years join countries on 
countries.id = population_years.country_id where 
year ='2007' and population !='Null' order by population limit 1

Query Results
population	name
0.00216	Niue


/* -- What is the average population of Poland during the time period covered by this dataset? */

select round(avg(population),2) as average_population,name  from population_years join countries on 
countries.id = population_years.country_id where 
name = 'Poland';

Query Results
average_population	name
38.56	Poland


/*-- How many countries have the word "The" in their name?*/

select name from countries where name like '%The%'

Query Results
name
Bahamas, The
Netherlands Antilles
Netherlands
Gambia, The



/* -- What was the total population of each continent in 2010? */

select sum(population) as total_population ,continent  from population_years join countries on 
countries.id = population_years.country_id where 
year ='2010' group by continent

Query Results
total_population	continent
1015.47846	Africa
4133.09148	Asia
723.06044	Europe
539.79456	North America
34.95696	Oceania
396.58235	South America
