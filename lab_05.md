```sql
#1.
delete from postac
where nazwa <> 'Bjorn'
and rodzaj = 'wiking'
order by data_ur asc limit 2;

alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
alter table walizka drop foreign key walizka_ibfk_1

alter table postac modify id_postaci int

alter table postac drop primary key

#2.
alter table postac add column pesel char(11) first
update postac set pesel='65644351234'+id_postaci;
alter table postac
add primary key(pesel)

alter table postac modify rodzaj enum('wiking','ptak','kobieta','syrena')

insert into postac(pesel,id_postaci, nazwa, rodzaj, data_ur, wiek) values('12345678910','7','Gertruda Nieszczera','syrena','2010-01-20','13')

#3.
update postac set statek = "Ragnarok"
where nazwa like '%a%';

update postac set max_ladownosc =max_ladownosc* 0.1
where data_wodowania between '1901-01-01'AND '2000-12-31' ;

select wiek from postac 
where wiek <=1000

#4.
insert into postac(pesel,id_postaci,nazwa,data_ur,wiek) values ('12121212121','8','Loko','1999-02-20','24')

create table marynarz like postac
insert into marynarz select * from postac where statek is not null

alter table marynarz add foreign key(statek) references statek(nazwa_statku)

#5.
update postac set statek=null where statek is not null

delete from postac where nazwa ='Olaf'

alter table postac drop foreign key postac_ibfk_1
alter table marynarz drop foreign key marynarz_ibfk_1
alter table statek drop primary key
delete from statek where nazwa_statku is not null

drop table statek

create table zwierz(
id int primary key auto_increment,
nazwa varchar(20),
wiek int
)

insert into zwierz select id_postaci, nazwa, wiek from postac where rodzaj = 'ptak'
insert into zwierz select id_postaci, nazwa, wiek from postac where nazwa='Loko'
'''
