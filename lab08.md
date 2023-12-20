# Zadanie 1 1.
```sql
insert into infs_kasperekk.kreatura select * from wikingowie.kreatura


create table infs_kasperekk.uczestnicy select * from wikingowie.uczestnicy
create table infs_kasperekk.etapy_wyprawy select * from wikingowie.etapy_wyprawy
create table infs_kasperekk.sektor select * from wikingowie.sektor
create table infs_kasperekk.wyprawa select * from wikingowie.wyprawa

```
# Zadanie 1   2.
```sql
select k.nazwa
from kreatura k left join uczestnicy u on u.id_uczestnika=k.idkreatury where u.id_uczestnika is null
```
# Zadanie 1   3.
```sql
select w.nazwa, sum(e.ilosc) from wyprawa w inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join ekwipunek e on w.id_wyprawy = e.idEkwipunku group by w.nazwa

```
# Zadanie 2   1.
```sql
select w.nazwa, count(u.id_uczestnika), group_concat(k.nazwa separator ' | ') as 'nazwa wyprawy'  from wyprawa w inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join kreatura k on u.id_uczestnika=k.idKreatury group by w.nazwa;
```
# Zadanie 2   2.
```sql
select w.nazwa, s.nazwa,w.kierownik,e.idEtapu from wyprawa w  inner join etapy_wyprawy e on w.id_wyprawy = e.idWyprawy
inner join kreatura k on w.kierownik=k.idKreatury
inner join sektor s on e.sektor=s.id_sektora
order by w.data_rozpoczecia, e.kolejnosc



```
