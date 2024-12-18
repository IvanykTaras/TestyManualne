<!-- 

<details><summary><h1>  </h1></summary>

</details>

---

<details><summary><h4>  </h4></summary>

</details> 

-->


link
https://gitlab.corcode.com/corcode/internal-helpdesk/-/issues/10967
https://gitlab.corcode.com/corcode/enterprise-helpdesk/-/issues/1499
https://gitlab.corcode.com/corcode/internal-helpdesk-ext/-/issues/1126

### Opis
> Oddział Katowice, do którego powinny być migrowane pojazdu rozpoczynające wynajem w Katowicach w 99rent, ma siedzibę w Ożarowicach.

> W związku z tym należy do systemu dodać nowe pole, które pozwoli na zdefiniowanie, że do danego oddziału CHP należy migrować pojazdy z podanej lokalizacji 99rent.

### Testy od Filipa
###### Testy

- Skonfigurować nowe pole dla wybranego oddziału i wykonać migrację pojazdu z systemu dev 99rent do dev CHP poprzez rozpoczęcie wynajmu z 99rent do CHP w systemie 99
- Jeśli istnieje oddział z odpowiednim miastem w nowym polu, to pojazd powinien trafić do niego po rozpoczęciu wynajmu z 99

###### After deployment steps

- Ustawić wartość 'Katowice' dla oddziału w Ożarowicach


### Pomysły jak zepsuć
- klika oddziałów mają ten sam oddział 99rent
- dodany samochód po wydaniu z 99rent posiada nr. rej który już istnieje w systemie chp

### Testy

##### Before Each
- [ ] Dodaje nowy pojazd **(dev 99)**
	- **Oddział:** Kraków 
	- **Dostępny teraz**: Tak
	- **Numer rej.:** KRK6667
- [ ] Dodaje rezerwacje z powyższym samochodem **(dev 99)** 
	- Oddział wydania i zwrotu **Kraków**
	- typ rezerwacji 
		- franczyza
		- nazwa: enterprise


<details><summary>Open</summary>

##### TC001 Samochód 99rent z rezerwacją o typie Enterprise integruje się z CHPem
- [ ] Przypisuje do oddziału w Warszawie odpowiadający oddział 99rent **Kraków** **(dev CHP)**
- [ ] wydaje rezerwację **(dev 99)**
- [ ] sprawdzam czy pojawił się samochód z numerem rej. KRK6667 **(dev CHP)**
- [ ] odbieram samochód **(dev 99)**
- [ ] sprawdzam czy zniknął samochód z numerem rej. KRK6667 **(dev CHP)**

</details>

**Efekt końcowy:** Pozytywny
##### TC002 Co się stanie kiedy kilka oddziałów CHP posiadają ten sam oddział 99rent
- [ ]  Przypisuje do oddziałów w Warszawie, Kraków, NIC, Jasło odpowiadający oddział 99rent **Kraków** **(dev CHP)**
- [ ] wydaje rezerwację **(dev 99)**
- [ ] sprawdzam czy pojawił się samochód z numerem rej. KRK6667 **(dev CHP)**
	- Pojawił się jeden pomyślny samochód w Oddziale  Warszawa 
- [ ] odbieram samochód **(dev 99)**
- [ ] sprawdzam czy zniknął samochód z numerem rej. KRK6667 **(dev CHP)**

**Efekt końcowy:** Pozytywny.

##### TC003  dodany samochód po wydaniu z 99rent posiada nr. rej który już istnieje w systemie chp
- [ ] Przypisuje do oddziału w Warszawie odpowiadający oddział 99rent **Kraków** **(dev CHP)**
- [ ] Dodaje nowy pojazd **(dev CHP)**
	- **Numer rej.:** KRK6667
- [ ] Wyświetla się komunikat że pojazd z takim nr. rej już istnieje 

**Efekt końcowy:** Pozytywny.






