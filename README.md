# MessageOk Editor

Textový editor jednotlivých boxů v editoru scénářů nabízí řadu možností, jak přizpůsobovat zobrazování textu v závislosti na různých datech. Díky tomu, lze dynamicky vypisovat to, co uživatel zadal při práci se scánéřem a nebo na základě zadání jednoduše upravovat to, co uživateli nabídneme za další možnosti. 

Mimo to, v textovém editoru lze ještě používat funkce pro skloňování a formátování proměnných a nebo pro vygenerování speciálních ovládacích prvků i mimo jejich standardní umístění.

## Vložení proměnné

Nejčastějším způsobem použití je vypsání proměnné. Proměnná může mít své vlastní jméno (typicky pokud si vstup od uživatele pojmenujete vlastním výrazem) a nebo můžete použít automatické vytváření proměnných z jednotlivých boxů. V praxi to znamená to, že každá odpověď uživatele (ať už psaná nebo formou výběru tlačítka) se ukládá jako proměnná s číslem boxu.

**Vypsání proměnné ``email``**

```
Zadali jste následující e-mail: {{email}}
```

**Vypsání toho, co uživatel zadal v boxu č. 3**

```
V hlavním menu jste si vybrali {{3}}
```

## Syntaxe

Základem je porozumnění toho v jakém formátu proměnné, funkce a podmínky do editoru vkládáme. Nejdůležitějším znakem jsou složené závorky: ``{``a ``}``. Tyto znaky symboly najdete na své klávesnici. Zkuste různé kombinace s klávesy Shift a Alt. Případně, pro Windows můžete vložit znak { stiskem klávesy ALT+123 a ALT+125 pro }.

Všechny proměnné i funkce se vždy uvádají **dvěma** znaky složených závorek, tedy: ``{{``

Každá proměnná i funkce musí být zároveň **vždy ukončena** dvojicí složených závorek, tedy: ``}}``

*Pozor, mezi složenými závorkami ``{`` nesmí být nikdy mezera.*

| Špatně      | Správně   |
|-------------|-----------|
| ``{ {nazev} }`` | ``{{nazev}}`` |
| ``{ { nazev } }`` | ``{{nazev}}`` |
| ``{{ nazev }}`` | ``{{nazev}}`` |
| ``{{nazev}``  | ``{{nazev}}`` |
| ``{nazev}`` | ``{{nazev}}`` |
