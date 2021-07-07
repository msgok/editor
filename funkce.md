# Funkce

Funkce rozšiřují základní možnosti zobrazení obsahu proměnné a nebo základní podmínky.

Funkce se používají podobně jako podmínky nebo proměnné. Rozdíl je v tom, že standarně dovolují vstup více parametrů. Pravidla jsou následující:
 - Každý parametr se odděluje mezerou.
 - Pokud má být parametrem konkrétní text, píše se v uvozovnách např. ``"Text k zobrazení"``
 - Pokud má být parametrem proměnná, píše se bez uvozovek (v případě objektu lze použít tečku k určení přesné cesty), např. ``nazevpromenne`` nebo ``api.hodnota``
 - Pokud má být parametrem logická hodnota (tedy ``true`` nebo ``false``) zapisuje se stejně jako proměnná, tedy bez uvozovek.
 
Příklady správného zápisu uvádíme u jednotlivých funkcích.

**Seznam funkcí**
- [date](#funkce-date)
- [inflect](#funkce-inflect)
- [button](#funkce-button)
- [#compare](#funkce-compare)
- [#exist](#funkce-exist)
- [#notexist](#funkce-notexist)
- [qrpay](#funkce-qrpay)
- [currency](#funkce-currency)
- [progress](#funkce-progress)

## Funkce ``date``

Slouží k úpravě formátu data a času. Běžně se při práci s API a dalšími systémy používá zápis pro datum ve formátu ``2020-09-01``, což není zcela obvyklé pro ne-IT prostředí. Tato funkce vám pomůže převést datum do srozumitelnější podoby.

```handlebars
{{date X "Y"}}
```

**Parametry**
 - ``date`` název funkce
 - ``X`` zdrojové datum *(konkrétní text nebo proměnná)*
 - ``Y`` formát data viz níže *(text)*
 
 **Formát data**
 - ``YYYY`` vypíše rok (4 číslice, např. 2020)
 - ``YY`` vypíše rok (2 číslice, napč. 99)
 - ``MM`` vypíše měsíc (2 číslice, např. 03)
 - ``M`` vypíše měsíc (1-2 číslice, např. 9)
 - ``Q`` vypíše číslo kvartálu (1 číslice, např. 3)
 - ``DD`` vypíše den v měsici (2 číslice, např. 03)
 - ``D`` vypíše den v měsíci (1-2 číslice, např. 9)
 - ``HH`` vypíše hodinu (2 číslice, např. 03)
 - ``H`` vypíše hodinu (1-2 číslice, např. 9)
 - ``mm`` vypíše minutu (2 číslice, např. 03)
 - ``m`` vypíše minutu (1-2 číslice např. 9)
 - ``ss`` vypíše sekundu (2 číslice, např. 03)
 - ``s`` vypíše sekundu (1-2 číslice, např. 9)

Příklady

```handlebars
{{date "2 years ago" "YYYY-MM-DD"}}
```

Vypíše: ``2018-09-01`` (dnešní datum před dvěma lety)

```handlebars
{{date ordered "D.M."}}
```

Vypíše: ``14.2.`` (datum z proměnné ``ordered`` převede do formátu ``14.2.``)

```handlebars
{{date ordered "DD.MM.YYYY"}}
```
Vypíše: ``01.02.2020`` (datum z proměnné ``ordered`` převede do formátu ``01.02.``)

## Funkce ``inflect``

Slouží k správnému skloňování na základě jednotlivých tvarů (např. 1 objednávka, 2 objednávky, 10 objednávek).

```handlebars
{{inflect A "B" "C" "D" E}}
```

**Parametry**
 - ``inflect`` název funkce
 - ``A`` zdrojové množství *(číslo nebo list)*
 - ``B`` tvar slova pro jedeno množství *(text)*
 - ``C`` tvar slova pro dvě až pět množství *(text)*
 - ``D`` tvar slova pro více než pět množství *(text)*
 - ``E`` zobrazit také množství *(logická hodnota true nebo false, výchozí false)*

Příklady

```handlebars
{{inflect orders "objednávka" "objednávky" "objednávek" true}}
```

Vypíše: ``13 objednávek`` (proměnná ``orders`` je číslo 13)

```handlebars
{{inflect items "zásilka" "zásilky" "zásilek"}}
```

Vypíše: ``zásilky`` (proměnná ``items`` je číslo 4)



## Funkce ``button``

Slouží k zobrazení tlačítka v prostoru obsahu zprávy, které přesune zákazníka na zadané číslo boxu.

```handlebars
{{button A "B"}}
```

**Parametry**
 - ``button`` název funkce
 - ``A`` ID boxu *(číslo)*
 - ``B`` Název tlačítka *(text)*
 
Příklady

```handlebars
{{button 21 "Pokud nevidíte svou objednávku, klikněte zde"}}
```

Zobrazí tlačítko s textem ``Pokud nevidíte svou objednávku, klikněte zde``, které zákazníka přesune na box s číslem 21.




## Funkce ``#compare``

Slouží složitějšímu vyhodnocování podmínek. Běžné použití ``#exist`` nebo ``#notexist`` kontroluje jen zda proměnná existuje nebo neexistuje. Díky funkci ``#compare`` můžete provádět složitější porovnávání (zda se proměnná rovná nějaké hodnotě, nebo je větší apod.).

```handlebars
{{#compare A "B" C}}X{{/compare}}
```

*Pozor, jedná se o tzv. blokovou funkci (poznáte podle znaku ``#`` na začátku), která sama o sobě nic nevypisuje, ale naopak vypíše nebo nevypíše to co zapíšete do jejího obsahu (X)*

**Parametry**
 - ``#compare`` název funkce
 - ``A`` první proměnná *(číslo, text, proměnná)*
 - ``B`` operátor viz níže *(text)*
 - ``C`` druhý proměnná *(číslo, text, proměnná)*
 
**Seznam operátorů**
 - ``is`` pokud se zadaná proměnná ``A`` rovná proměnné ``B``
 - ``=`` pokud se zadaná proměnná ``A`` rovná proměnné ``B``
 - ``!=`` pokud se zadaná proměnná ``A`` nerovná proměnné ``B``
 - ``not`` pokud se zadaná proměnná ``A`` nerovná proměnné ``B``
 - ``>`` pokud je proměnná ``A`` větší než proměnná ``B``
 - ``>=`` pokud je proměnná ``A`` větší nebo rovna proměnné ``B``
 - ``<`` pokud je proměnná ``A`` menší než proměnná ``B``
 - ``<=`` pokud je proměnná ``A`` menší nebo rovna proměnné ``B``

Příklady

```handlebars
{{#compare price ">" 1000}}Objednávka má hodnotu větší než 1000{{/compare}}
```

Vypíše: ``Objednávka má hodnotu větší než 1000`` (proměnná ``price`` je číslo 2500)


```handlebars
{{#compare 123 "is" "Storno"}}Storno provádíme jen na telefonním čísle 800123456{{/compare}}
```

Vypíše: ``Storno provádíme jen na telefonním čísle 800123456`` (proměnná ``123`` obsahuje název tlačítka "Storno")

```handlebars
{{#compare email1 "!=" email2}}Zadené e-maily nejsou stejné{{/compare}}
```

Vypíše: ``Zadené e-maily nejsou stejné`` (proměnná ``email1`` info@messageok.com a ``email2`` je hello@messageok.com)


## Funkce ``qrpay``

Vygeneruje obrázek pro QR platbu (používá API od qrplatba.cz).

```handlebars
{{qrpay "A" "B" "C" "D" "E"}}
```

**Parametry**
 - ``qrpay`` název funkce
 - ``A`` typ QR kódu *(hodnota: "cz" nebo "iban")*
 - ``B`` číslo bankovního účtu nebo iban *(text, tzn. číslo účtu může být včetně předvolby nebo iban)*
 - ``C`` kód banky nebo BIC *(číslo nebo text)*
 - ``D`` částka *(číslo)*
 - ``E`` variabilní symbol nebo reference *(číslo nebo text)*

Volitelně lze přidat ještě další dva parametry: měnu *(text)* a velikost v px *(číslo)*, viz příklady.
 
Příklady 

```handlebars
{{qrpay "cz" "123123123" "0100" "499" "20200001"}}
```

Vygeneruje obrázek s QR kódem pro platbu částky 499 Kč na účet 123123123/0100 s VS 20200001.

```handlebars
{{qrpay "cz" "123123123" "0100" order.amount order.vs}}
```

Vygeneruje obrázek s QR kódem pro platbu na účet 123123123/0100 s částkou načtenou z proměnné ``order.amount`` a VS načteným z ``order.vs``.

```handlebars
{{qrpay "iban" "CZ5508000000001234567899" "RZBCCZPP" "100" "20200001"}}
```

Vygeneruje obrázek s QR kódem pro platbu částky 100 EUR na účet CZ5508000000001234567899 s referencí 20200001.


```handlebars
{{qrpay "cz" "123123123" "0100" "150" "20200002" "EUR" "250"}}
```

Vygeneruje obrázek o velikosti 250px s QR kódem pro platbu částky 150 EUR na účet 123123123/0100 s VS 20200002.



## Funkce ``currency``

Upravuje zadané číslo na správný formát částky.

```handlebars
{{currency A" "B"}}
```

**Parametry**
 - ``currency`` název funkce
 - ``A`` číslo *(číslo nebo proměnná)*
 - ``B`` měna *(řetězec EUR nebo Kč (Kč je výchozí))*

Příklady

```handlebars
Zaplaťte prosím {{currency topay}} na náš bankovní účet.
```

Vypíše: ``Zaplaťte prosím 1 199,90 Kč na náš bankovní účet`` (proměnná ``topay`` obsahuje číslo ``1199.9``)

```handlebars
Zaplaťte prosím {{currency topayeur "EUR"}} na náš bankovní účet.
```

Vypíše: ``Zaplaťte prosím 99,99 € na náš bankovní účet`` (proměnná ``topayeur`` obsahuje číslo ``99.99``)



## Funkce ``progress``

Zobrazuje grafický progress bar, který zobrazuje jednotlivé stavy.

```handlebars
{{progrss A "B" "C"}}
```

**Parametry**
 - ``progress`` název funkce
 - ``A`` až po jaký krok má být progress aktivní *(číslo nebo proměnná)*
 - ``B`` název ikonky
 - ``C`` název kroku

Příklady

```handlebars
{{progrss 1 "ico-delivery" "Doručeno"}}
```
