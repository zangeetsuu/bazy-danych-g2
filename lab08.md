```sql
insert into infs_kasperekk.kreatura select * from wikingowie.kreatura


create table infs_kasperekk.wyprawa select * from wikingowie.wyprawa


select k.nazwa
from kreatura k left join uczestnicy u on u.id_uczestnika=k.idkreatury where u.id_uczestnika is null



select w.nazwa, sum(e.ilosc) from wyprawa w inner join uczestnicy u on w.id_wyprawy=u.id_wyprawy
inner join ekwipunek e on w.id_wyprawy = e.idEkwipunku group by w.nazwa


select w.nazwa, count(u.id_uczestnika), k.nazwa, group_concat(w.nazwa separator '|') as 'nazwa wyprawy'  from w.wyprawa inner join uczetnicy u on w.id_wyprawy=u.id_uczestnika
inner join kreatury k on w.id_wyprawy=k.nazwa group by w.nazwa



```
