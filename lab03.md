# lab_03

```sql
create table postac (
id_postaci int not null primary key auto_increment,
nazwa varchar(40),
rodzaj enum('wiking', 'ptak', 'kobieta'),
data_ur date,
wiek int unsigned );

# b)
insert into postac values (1,'Bjorn', 'wiking', '1750-02-25', 44);
insert into postac values (2,'Drozd', 'ptak', '2023-09-13', 1);
insert into postac values (3, 'Tesciowa', 'kobieta', '1960-10-25', 63);

# c)
update postac 
set wiek = 88 
where nazwa = 'Tesciowa';

# Zad.2 
# a)
create table walizka (
id_walizki int not null primary key auto_increment,
pojemnosc int unsigned,
kolor enum('różowy', 'czerwony', 'tęczowy', 'żółty'),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci)
);

# b)

alter table walizka
alter column kolor set default 'różowy';

# c)
insert into walizka values(1, 10, 'czerwony', 1);
insert into walizka values(2, 5, 'tęczowy', 3);

# Zad. 3
# a)
create table izba(
	adres_budynku varchar(50) not null,
	nazwa_izby varchar(50) not null,
	metraz int unsigned,
	wlasciciel int,
    primary key(adres_budynku, nazwa_izby),
	foreign key (wlasciciel) references postac(id_postaci) on delete set null
);
#b)
alter table izba
add column kolor varchar (20) default 'czarny'
after metraz;
#c)
insert into izba values ('Sielska 50', 'spiżarnia', default, 1);

#zad.4
#a)

create table przetwory(
id_przetworu int Primary key Auto_increment,
rok_produkcji smallint default 1684,
id_wykonawcy int,
zawartosc varchar(50),
dodatek varchar(50) default 'chilli',
id_konsumenta int,
foreign key(id_wykonawcy) references postac(id_postaci),
foreign key(id_konsumenta) references postac(id_postaci)
);
#b)
insert into przetwory values( 1, 2023, 3, 'Bigos', default, 1)
#zad5
#a)
insert into postac(nazwa,rodzaj,data_ur,wiek) values('Bard','wiking','1920-01-20',103);
insert into postac(nazwa,rodzaj,data_ur,wiek) values('Hammerfal','wiking','1926-02-20',22);
insert into postac(nazwa,rodzaj,data_ur,wiek) values('Olaf','wiking','1938-07-20',66);
insert into postac(nazwa,rodzaj,data_ur,wiek) values('Berserk','wiking','1915-04-20',33);
insert into postac(nazwa,rodzaj,data_ur,wiek) values('Greg','wiking','1912-11-20',45);

#b)
create table statek(
nazwa_statku varchar(10) not null,
rodzaj_statku enum('karli','snek','skeid','drakar'),
data_wodowania date,
max_ladownosc int unsigned,
primary key(nazwa_statku)
);
#c)
insert into statek values('Ragnarok','drakar','1820-01-23',10000);
insert into statek values('Asgard','drakar','1820-01-23',10000);
#d)
alter table postac add column funkcja varchar(40);
#e)
update postac set funkcja = 'kapitan' where id_postaci = 1
#f)
alter table postac add foreign key(statek) references statek(nazwa_statku)
#g)
update postac set statek = 'Ragnarok' where rodzaj = 'wiking';
update postac set statek = 'Asgard' where rodzaj = 'ptak';
#h)
delete from izba where nazwa_izby = 'spiżarnia';
#i)
drop table izba;

