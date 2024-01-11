# Zadanie 1
```sql
SELECT imie, nazwisko, data_urodzenia FROM __firma_zti.pracownik;
```
# Zadanie 2
```sql
SELECT imie, nazwisko, year(now())-year(data_urodzenia) as wiek FROM __firma_zti.pracownik;
```
# Zadanie 3
```sql
select d.nazwa, count(p.id_pracownika) as liczba_pracownikow from __firma_zti.dzial 
inner join __firma_zti.pracownik p on p.dzial=d.id_dzialu group by d.nazwa
```
# Zadanie 4
```sql
select k.nazwa_kategori, count(t.id_towaru) as liczba_produktow from kategoria k 
inner join towar t on t.kategoria=k.id_kategori group by k.nazwa_kategori
```

# Zadanie 5 
```sql
select k.nazwa_kategori, group_concat(t.nazwa_towaru)  from kategoria k 
inner join towar t on t.kategoria=k.id_kategori group by k.nazwa_kategori
```
# Zadanie 6
```sql
select Round(avg(pensja), 2) from pracownik

```
# Zadanie 7
```sql
select Round(avg(pensja), 2) from pracownik where year(now()) - year(data_zatrudnienia)<=5
```
# Zadanie 8
```sql
select t.nazwa_towaru from pozycja_zamowienia p 
inner join towar t on t.id_towaru = p.towar
group by t.nazwa_towaru  order by count(p.towar) desc limit 10

```
# Zadanie 9
```sql
SELECT z.numer_zamowienia,sum(p.cena*p.ilosc) as wartosc FROM zamowienie z
inner join pozycja_zamowienia p on p.zamowienie=z.id_zamowienia where z.data_zamowienia between '2017-01-01' and '2017-03-31' 
group by z.numer_zamowienia
```
# Zadanie 10
```sql
select p.imie, p.nazwisko, sum(pz.cena*pz.ilosc) as wartosc from pracownik p
inner join zamowienie z on p.id_pracownika=z.pracownik_id_pracownika
inner join pozycja_zamowienia pz  on z.id_zamowienia=pz.zamowienie
group by id_pracownika  order by sum(cena*ilosc) desc
```
