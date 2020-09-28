# Podmínky

Podmínky umožňují v jednom boxu zobrazovat různé stavy na základě hodnot proměnných.

## Jednoduchá podmínka

Speciální syntaxí je možné také vytvářet jednoduché podmínky, které reagují na to, zda proměnná existuje nebo nikoliv. Pokud tedy chcete řádek se zadaným e-mailem vypsat jen pokud byl e-mail zadaný, můžete to provést následujícími způsoby.

```handlebars
{{#email}}Na zadaný e-mail {{email}} vám zašleme potvrzení.{{/email}}
```

Speciální znak ``#`` na začátku říká, že se jedná o podmínku, která kontroluje existenci proměnné ``email``. 

Zároveň je nutné podmínku také ukončit. K tomu slouží znak ``/``, následující názvem proměnné z podmínky, kterou kontrolujeme. Tím se podmínka ukončí.

Podobným způsobem můžete vytvořit negativní podmínku:

```handlebars
{{^email}}Nezadali jste e-mail, takže potvrzení vám zasílat nebudeme.{{/email}}
```

Speciální znak ``^`` na začátku říká, že se jedná o negativní podmínku, která kontroluje neexistenci proměnné ``email``. 

Stejně jako v předchozím případě je nutné podmínku také ukončit. K tomu slouží opět znak ``/``, následující názvem proměnné z podmínky, kterou kontrolujeme. Tím se podmínka ukončí.


## Podmínky buď a nebo

Pro složitější podmínky se hodí [funkce](funkce.md) ``#if``. Která má následující syntaxi:

```handlebars
{{#if email}}
  Na zadaný e-mail {{email}} vám zašleme potvrzení.
{{/if}}
```
Na rozdíl od jednoduchého zápisu výše, lze v rámci funkce ``#if`` použí také zápis obsluhující variantu pro neexistující proměnnou:

```handlebars
{{#if email}}
  Na zadaný e-mail {{email}} vám zašleme potvrzení.
{{else}}
  Nezadali jste e-mail, takže potvrzení vám zasílat nebudeme.
{{/if}}
```

Zároveň lze podmínky rozšířit o další varianty:

```handlebars
{{#if email}}
  Na zadaný e-mail {{email}} vám zašleme potvrzení.
{{else if telefon}}
  Nezadali jste e-mail, ale zadali jste telefon, takže obdržíte SMS.
{{else}}
  Nezadali jste ani e-mail ani telefon.
{{/if}}
```

Podobně jako ``#if`` funguje také opačná varianta a to funkce ``#unless`` která řeší opak existence proměnné, tedy to, zda neexistuje. Předchozí příklad by se tedy dal zapsat následujícím způsobem:

```handlebars
{{#unless telefon}}
  Nezadali jste telefon.
{{else unless email}}
  Nezadali jste e-mail.
{{else}}
  Zadali jste e-mail i telefon.
{{/if}}
```

Uvedené podmínky s využitím ``#if`` nebo ``#unless`` vždy fungují tak, že kontrola podmínek se vždy zastaví na prvním pozitivním vyhodnocení. Je tedy důležité jejich pořadí a také to, jak uvedené proměnné vytváříte ve scénáři. Pokud se zákazníka nejprve ptáte na ``telefon`` a až v druhém kroku na ``email`` měla by tomu odpovídat i uvedená podmínka a nejprve kontrolovat zda je zadán ``telefon`` a až v druhém kroku, zda je zadán ``email``. V opačném případě by podmínka vždy skončila na prvním kroku.

## Kombinace podmínek

Podmínky s využitím funkce ``#if`` i v základním, zjednodušeném zápisu lze kombinovat. Zcela správné jsou tedy následující příklady:

```handlebars
{{#if email}}
  {{#if telefon}}
    Zadali jste e-mail i telefon
  {{/if}}
{/if}
```

```handlebars
{{#email}}
{{#telefon}}
Zadali jste e-mail i telefon
{{/telefon}}
{{/email}}
```

Pokud používáte funkci ``#if`` lze její zápis kombinovat s funkcí ``#unless``, tedy například následujícími způsoby:

```handlebars
{{#if telefon}}
  Zadali jste telefon.
{{else unless email}}
  Nezadali jste telefon ani e-mail.
{{else}}
  Zadali jste e-mail, ale nezadali telefon.
{{/if}}
```

```handlebars
{{#unless telefon}}
  Nezadali jste telefon.
{{else if email}}
  Zadali jste telefon, a zadali jste i e-mail.
{{else}}
  Nezadali jste e-mail, ale zadali jste telefon.
{{/unless}}
```
