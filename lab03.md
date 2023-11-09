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
create table izba (
adres_budynku
```

