```sql
create table kreatura(
idkreatury int(11) primary key auto_increment,
nazwa varchar(30),
rodzaj varchar(3),
dataUr date ,
waga int(10),
udzwig int(10)
)

create table zasob(
idZasobu int(11) primary key auto_increment,
nazwa varchar(30),
waga float(6,2),
ilosc int(10),
dataPozyskania date,
rodzaj varchar(50)
)

create table ekwipunek(
idEkwipunku int(11) primary key auto_increment,
idKreatury int(11),
idZasobu int(11),
ilosc int(10)
)




insert into zasob select * from wikingowie.zasob

select * from zasob where rodzaj = "jedzenie"

select idZasobu, ilosc from ekwipunek where idKreatury in (1,3,5)

select * from kreatura where rodzaj <> "wiedzma" and udzwig>=50

select * from zasob where waga between 2 and 5

select * from kreatura where nazwa like '%or%' and udzwig between 30 and 70

select * from zasob where month(dataPozyskania) = 7 or month(dataPozyskania) = 08;

select * from zasob where rodzaj is not null order by waga asc

select * from kreatura order by dataUr asc limit 5

select distinct rodzaj from zasob

select nazwa, rodzaj from kreatura where rodzaj like 'wi%'

select ilosc*waga as waga from zasob  where year(dataPozyskania) between 2000 and 2007

select waga*0.3 as wagaWlasciwa from zasob where rodzaj = "jedzenie";

select  waga*0.7 as wagaOdpadkow from zasob where rodzaj = "jedzenie";

select * from zasob where rodzaj is null

select distinct rodzaj from zasob where nazwa like 'Ba%' or '%os' order by rodzaj




```
