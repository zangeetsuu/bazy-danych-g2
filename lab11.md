# Zadanie 1
```sql
select d.nazwa,  max(p.pensja), min(p.pensja), avg(pensja) from dzial d
inner join pracownik p on p.dzial=d.id_dzialu
group by p.dzial
```
# Zadanie 2
```sql
select k.pelna_nazwa, sum(pz.ilosc*pz.cena) from klient k
inner join zamowienie z on z.klient = k.id_klienta
inner join pozycja_zamowienia pz on pz.zamowienie=z.id_zamowienia
group by pelna_nazwa order by sum(ilosc*cena) desc limit 10 
```
# Zadanie 3 
```sql
select year(z.data_zamowienia) as rok, sum(pz.ilosc*pz.cena) as przychod from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie
inner join pracownik p on p.id_pracownika=z.pracownik_id_pracownika
group by year(z.data_zamowienia) order by sum(ilosc*cena) desc
```
# Zadanie 4
```sql
select sz.nazwa_statusu_zamowienia, sum(pz.ilosc*pz.cena) as wartosc from pozycja_zamowienia pz
inner join zamowienie z on z.id_zamowienia=pz.zamowienie
inner join status_zamowienia sz on sz.id_statusu_zamowienia=z.status_zamowienia
where id_statusu_zamowienia=6 group by nazwa_statusu_zamowienia
```
# Zadanie 5
```sql
select count(pz.zamowienie) as liczba_zamowien, sum(pz.ilosc*pz.cena) as suma_zamowien, ak.miejscowosc from pozycja_zamowienia pz
inner join zamowienie z on pz.zamowienie=z.id_zamowienia
inner join adres_klienta ak on ak.klient=z.klient
where typ_adresu=1
group by miejscowosc 

```
# Zadanie 6 
```sql
select sum(pz.ilosc*pz.cena)-sum(t.cena_zakupu) as dochod from pozycja_zamowienia pz
inner join zamowienie z on z.id_zamowienia= pz.zamowienie
inner join towar t on pz.towar=t.id_towaru
where status_zamowienia = 5
```
# Zadanie 7
```sql
select sum(pz.ilosc*pz.cena)-sum(t.cena_zakupu) as dochod,year(data_zamowienia) as rok from pozycja_zamowienia pz
inner join zamowienie z on z.id_zamowienia= pz.zamowienie
inner join towar t on pz.towar=t.id_towaru
group by rok
```
# Zadanie 8
```sql
select sum(sm.ilosc*pz.cena) as wartosc_stanu, k.nazwa_kategori from stan_magazynowy sm
inner join towar t on sm.towar=t.id_towaru
inner join kategoria k on t.kategoria=k.id_kategori
inner join pozycja_zamowienia pz on pz.towar=t.id_towaru
group by nazwa_kategori

```
# Zadanie 9 
```sql
select monthname(data_urodzenia) as miesiąc, count(id_pracownika) as Liczba_pracowników from pracownik 
group by miesiąc order by month(miesiąc) desc

```

# Zadanie 10 
```sql
select imie, nazwisko, sum(pensja) from pracownik
 where  data_zatrudnienia <= CURRENT_DATE group by id_pracownika

```
