# MessageOk Editor

Textový editor jednotlivých boxů v editoru scénářů nabízí řadu možností, jak přizpůsobovat zobrazování textu v závislosti na různých datech. Díky tomu, lze dynamicky vypisovat to, co uživatel zadal při práci se scánéřem a nebo na základě zadání jednoduše upravovat to, co uživateli nabídneme za další možnosti. 

Mimo to, v textovém editoru lze ještě používat funkce pro skloňování a formátování proměnných a nebo pro vygenerování speciálních ovládacích prvků i mimo jejich standardní umístění.

## Syntaxe

Základem je porozumnění toho v jakém formátu proměnné, funkce a podmínky do editoru vkládáme. Nejdůležitějším znakem jsou složené závorky: ``{``a ``}``. Tyto znaky symboly najdete na své klávesnici. Zkuste různé kombinace s klávesy Shift a Alt. Případně, pro Windows můžete vložit znak { stiskem klávesy ALT+123 a ALT+125 pro }.

Všechny proměnné i funkce se vždy uvádají **dvěma** znaky složených závorek, tedy: ``{{``

Každá proměnná i funkce musí být zároveň vždy ukončena dvojicí složených závorek, tedy: ``}}``

*Pozor, mezi složenými závorkami ``{`` nesmí být nikdy mezera.*

| Špatně      | Správně   |
|-------------|-----------|
| ``{ {nazev} }`` | ``{{nazev}}`` |
| ``{ { nazev } }`` | ``{{nazev}}`` |
| ``{{ nazev }}`` | ``{{nazev}}`` |
| ``{{nazev}``  | ``{{nazev}}`` |
| ``{nazev}`` | ``{{nazev}}`` |
