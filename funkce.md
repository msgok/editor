# Funkce

Funkce rozšiřují základní možnosti zobrazení obsahu proměnné a nebo základní podmínky.

Funkce se používají podobně jako podmínky nebo proměnné. Rozdíl je v tom, že standarně dovolují vstup více parametrů. Pravidla jsou následující:
 - Každý parametr se odděluje mezerou.
 - Pokud má být parametrem konkrétní text, píše se v uvozovnách např. ``"Text k zobrazení"``
 - Pokud má být parametrem proměnná, píše se bez uvozovek (v případě objektu lze použít tečku k určení přesné cesty), např. ``nazevpromenne`` nebo ``api.hodnota``
 - Pokud má být parametrem logická hodnota (tedy ``true`` nebo ``false``) zapisuje se stejně jako proměnná, tedy bez uvozovek.
 
Příklady správného zápisu uvádíme u jednotlivých funkcích:

## Funkce ``date``

Slouží k úpravě formátu data a času. Běžně se při práci s API a dalšími systémy používá zápis pro datum ve formátu ``2020-09-01``, což není zcela obvyklé pro ne-IT prostředí. Tato funkce vám pomůže převést datum do srozumitelnější podoby.

```handlebars
{{#date X "Y"}}
```

**Parametry**
 - ``#date`` název funkce
 - ``X`` zdrojové datum *(konkrétní text nebo proměnná)*
 - ``Y`` formát data *(text)*

Příklady

```handlebars
{{#date "2 years ago" "YYYY-mm-dd"}}
```

Vypíše: ``2018-09-01`` (dnešní datum před dvěma lety)

```handlebars
{{#date ordered "dd.mm."}}
```

Vypíše: ``14.2.`` (datum z proměnné ``ordered`` převede do formátu ``14.2.``)


## Funkce ``inflect``

Slouží k správnému skloňování na základě jednotlivých tvarů (např. 1 objednávka, 2 objednávky, 10 objednávek).

## Funkce ``inflect``

```handlebars
{{#inflect A "B" "C" "D" E}}
```

**Parametry**
 - ``#inflect`` název funkce
 - ``A`` zdrojové množství *(číslo nebo list)*
 - ``B`` tvar slova pro jedeno množství *(text)*
 - ``C`` tvar slova pro dvě až pět množství *(text)*
 - ``D`` tvar slova pro více než pět množství *(text)*
 - ``E`` zobrazit také množství *(logická hodnota true nebo false, výchozí false)*

Příklady

```handlebars
{{#inflect orders "objednávka" "objednávky" "objednávek" true}}
```

Vypíše: ``13 objednávek`` (proměnná ``orders`` je číslo 13)

```handlebars
{{#inflect items "zásilka" "zásilky" "zásilek"}}
```

Vypíše: ``zásilky`` (proměnná ``items`` je číslo 4)
