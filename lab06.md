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
```
