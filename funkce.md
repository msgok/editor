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

## Funkce ``date``

Slouží k úpravě formátu data a času. Běžně se při práci s API a dalšími systémy používá zápis pro datum ve formátu ``2020-09-01``, což není zcela obvyklé pro ne-IT prostředí. Tato funkce vám pomůže převést datum do srozumitelnější podoby.

```handlebars
{{date X "Y"}}
```

**Parametry**
 - ``date`` název funkce
 - ``X`` zdrojové datum *(konkrétní text nebo proměnná)*
 - ``Y`` formát data *(text)*

Příklady

```handlebars
{{date "2 years ago" "YYYY-mm-dd"}}
```

Vypíše: ``2018-09-01`` (dnešní datum před dvěma lety)

```handlebars
{{date ordered "dd.mm."}}
```

Vypíše: ``14.2.`` (datum z proměnné ``ordered`` převede do formátu ``14.2.``)


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

Slouží složitějšímu vyhodnocování podmínek. Běžné použití ``#if`` nebo ``#unless`` kontroluje jen zda proměnná existuje nebo neexistuje. Díky funkci ``#compare`` můžete provádět složitější porovnávání.

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
 - ``=`` pokud se zadaná proměnná ``A`` rovná proměnné ``B``
 - ``!=`` pokud se zadaná proměnná ``A`` nerovná proměnné ``B``
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
{{#compare email1 "!=" email2}}Zadené e-maily nejsou stejné{{/compare}}
```

Vypíše: ``Zadené e-maily nejsou stejné`` (proměnná ``email1`` info@messageok.com a ``email2`` je hello@messageok.com)
