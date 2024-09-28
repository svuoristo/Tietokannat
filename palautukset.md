05 Join

1. 
select country.name as "country name", airport.name as "airport name"
from airport
inner join country on country.iso_country = airport.iso_country
where country.name = "Finland";
<img width="693" alt="Näyttökuva 2024-09-11 kello 14 36 35" src="https://github.com/user-attachments/assets/5ff50bb8-3383-4061-b8d2-acd23a74b372">
<img width="693" alt="Näyttökuva 2024-09-11 kello 14 36 52" src="https://github.com/user-attachments/assets/12527f37-e61d-4c6f-9c40-e79f919a959e">


2.
select screen_name, name
from airport
inner join game on location = ident;
<img width="693" alt="Näyttökuva 2024-09-11 kello 15 06 24" src="https://github.com/user-attachments/assets/9debb864-840a-4a0e-be50-44f16ef4f2d2">

3.
select screen_name, country.name
from airport
inner join country on country.iso_country = airport.iso_country
inner join game on location = ident;
<img width="693" alt="Näyttökuva 2024-09-11 kello 15 07 51" src="https://github.com/user-attachments/assets/d4561757-16af-44ba-9776-1e1b76b09607">

4.
select name, screen_name
from airport
left join game on location = ident
where name like "%Hels%";
<img width="693" alt="Näyttökuva 2024-09-11 kello 15 08 07" src="https://github.com/user-attachments/assets/1c99fa3f-bb1d-4897-8c4e-6a321bc9bc2b">

5.
select name, screen_name
from goal_reached
right join goal on goal.id = goal_id
left join game on game.id = game_id;
<img width="693" alt="Näyttökuva 2024-09-11 kello 15 08 21" src="https://github.com/user-attachments/assets/07201305-d8e0-4e77-9f11-221cb3650d19">


05 Sisäkysely

1.
select country.name
from country
where iso_country in (
    select iso_country
    from airport
    where name like "Satsuma%");
<img width="358" alt="Näyttökuva 2024-09-28 kello 19 59 59" src="https://github.com/user-attachments/assets/c558b72f-f4a2-4683-ab89-671344fb42bd">

2.
select name
from airport
where iso_country in (
    select iso_country
    from country
    where name = "Monaco");
<img width="358" alt="Näyttökuva 2024-09-28 kello 20 03 48" src="https://github.com/user-attachments/assets/b0af5654-a33d-4939-838e-8117359fd37d">

3.
select screen_name
from game
where id in (
    select game_id
    from goal_reached
    where goal_id in (
        select id
        from goal
        where name = "CLOUDS"
        )
    );
  <img width="358" alt="Näyttökuva 2024-09-28 kello 20 08 47" src="https://github.com/user-attachments/assets/850554a5-2de3-4a6b-9008-91afdcdfa696">

4.
select name
from country
where iso_country not in (
    select iso_country
    from airport
    );
  <img width="358" alt="Näyttökuva 2024-09-28 kello 20 14 17" src="https://github.com/user-attachments/assets/f2b019fc-b7a5-4497-ae34-33101d75a19a">

5.
select name
from goal
where id not in (
    select goal_id
    from goal_reached
    where game_id in (
        select id
        from game
        where screen_name = "Heini"
        )
    );
    <img width="358" alt="Näyttökuva 2024-09-28 kello 20 18 20" src="https://github.com/user-attachments/assets/b1631c07-7285-457a-a71c-09ebc842cd35">


04 Koostekyselyt

1.
select max(elevation_ft)
from airport;
<img width="358" alt="Näyttökuva 2024-09-28 kello 21 10 55" src="https://github.com/user-attachments/assets/df644672-3db0-4122-907c-140dd466438a">

2.
select continent, count(*)
from country
group by continent;
<img width="358" alt="Näyttökuva 2024-09-28 kello 21 14 48" src="https://github.com/user-attachments/assets/bd936acb-3cdd-4bba-8e00-64a5543e2a1f">

3.
select screen_name, count(*)
from game
inner join goal_reached on game_id = id
group by screen_name;
<img width="358" alt="Näyttökuva 2024-09-28 kello 21 27 52" src="https://github.com/user-attachments/assets/07fbd44e-1e25-4228-a8ac-dc56a97db55d">

4.
select screen_name
from game
where co2_consumed in (
    select min(co2_consumed)
    from game
    );
<img width="358" alt="Näyttökuva 2024-09-28 kello 21 31 34" src="https://github.com/user-attachments/assets/d9a7e856-e564-4f89-8a86-674ebf989dd1">

5.
select country.name, count(*)
from country
inner join airport on airport.iso_country = country.iso_country
group by airport.iso_country
order by count(*) DESC
limit 50;
<img width="515" alt="Näyttökuva 2024-09-28 kello 21 38 54" src="https://github.com/user-attachments/assets/2492114c-8ddb-433d-a195-79d94d6b8cc7">

6.
select country.name
from country
inner join airport on airport.iso_country = country.iso_country
group by airport.iso_country
having count(*) > 1000;
<img width="515" alt="Näyttökuva 2024-09-28 kello 21 47 19" src="https://github.com/user-attachments/assets/474f513b-09e0-4f6c-be94-3f9975e89e6e">

7.
select name
from airport
where elevation_ft in (
    select max(elevation_ft)
    from airport
    );
<img width="515" alt="Näyttökuva 2024-09-28 kello 21 49 38" src="https://github.com/user-attachments/assets/a9d4c2e3-30ec-49e5-97da-53fda5a199f1">

8.
select country.name
from country
inner join airport on airport.iso_country = country.iso_country
where elevation_ft in (
    select max(elevation_ft)
    from airport);
<img width="515" alt="Näyttökuva 2024-09-28 kello 21 51 54" src="https://github.com/user-attachments/assets/e03261bd-2ee3-419c-bc6b-50bc8a1ed9d1">

9.
select count(*)
from game, goal_reached
where id = game_id and screen_name = "Vesa"
group by screen_name;
<img width="515" alt="Näyttökuva 2024-09-28 kello 21 58 02" src="https://github.com/user-attachments/assets/51fa27ff-a8f7-4deb-a1dd-74c82241d0e4">

10.
select name
from airport
where latitude_deg in (
    select min(latitude_deg)
    from airport);
<img width="515" alt="Näyttökuva 2024-09-28 kello 22 01 50" src="https://github.com/user-attachments/assets/abba8792-9cd8-42ba-b7c3-a831fe1dfb70">

04 Päivityskyselyt

1.
update game
set co2_consumed = (
    select co2_consumed + 500
    from game
    where screen_name = "Vesa"),
    location = (
        select ident
        from airport
        where name = "Nottingham Airport")
where screen_name = "Vesa";
<img width="515" alt="Näyttökuva 2024-09-28 kello 22 34 03" src="https://github.com/user-attachments/assets/7f021887-f559-4f51-a98f-0cb1d3892a54">

2.
delete from goal_reached;
<img width="515" alt="Näyttökuva 2024-09-28 kello 22 35 55" src="https://github.com/user-attachments/assets/c7fd1c91-3232-4b55-a1e9-8e4f14066f86">

3.
delete from game;
<img width="515" alt="Näyttökuva 2024-09-28 kello 22 36 42" src="https://github.com/user-attachments/assets/1ef8098a-879d-44bf-bb9f-6bf7bf0a76af">
