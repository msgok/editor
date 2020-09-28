# Podmínky

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

Pro složitější podmínky se hodí [funkce](funkce.md) ``#if``. Která má podobnou syntaxi:

```handlebars
{{#if email}}
  Na zadaný e-mail {{email}} vám zašleme potvrzení.
{{/if}}
```
