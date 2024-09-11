05
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

