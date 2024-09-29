
# Koostetieto kyselyt harjoitukset
# tehtävä1
select max(elevation_ft)
from airport;
![screenshot](tehtava1-5.png)

# tehtävä2
select continent, count(*)
from country
group by continent;
![screenshot](tehtava2-5.png)

# tehtävä3
select screen_name, count(*)
from game, goal_reached
where id = game_id
group by screen_name;
![screenshot](tehtava3-5.png)

# tehtävä4
select screen_name
from game 
where co2_consumed in(
select min(co2_consumed) 
from game 
);
![screenshot](tehtava4-5.png)

# tehtävä5
select country.name, count(*)
from country, airport
where airport.iso_country = country.iso_country
group by country.iso_country
order by count(*) DESC
limit 50;
![screenshot](tehtava5-5.png)

# tehtävä6
select country.name
from airport, country
where airport.iso_country = country.iso_country
group by country.iso_country
having count(*)>1000;
![screenshot](tehtava6-5.png)

# tehtävä7
select name
from airport
where elevation_ft in (
select max(elevation_ft)
from airport);
![screenshot](tehtava7-5.png)

# tehtävä8
select name
from country
where iso_country in(
select iso_country
from airport
where elevation_ft in(
select max(elevation_ft)
from airport)
);
![screenshot](tehtava8-5.png)

# tehtävä9
select count(*)
from goal
where id in(
select goal_id
from goal_reached
where game_id in (
select id
from game
where screen_name = "Vesa"));
![screenshot](tehtava9-5.png)


# tehtävä10
select name
from airport
where latitude_deg in(
select min(latitude_deg)
from airport
);
![screenshot](tehtava10-5.png)

# Päivityskyselyt harjoitukset:

# tehtävä1
update game
set location = (select ident from airport where name = "Nottingham Airport"),co2_consumed = co2_consumed+500
where screen_name = "Vesa";
![screenshot](tehtava1-1-5.png)

# tehtävä 2
![screenshot](tehtava2-1-5.png)

# tehtävä 3
delete from goal_reached;
![screenshot](tehtava3-1-5.png)

# tehtävä 4
delete from game;
![screenshot](tehtava4-1-5.png)
