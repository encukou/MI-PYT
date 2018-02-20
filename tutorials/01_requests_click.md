requests a click
================

Výukové materiály o virtuálním prostředí:
[naucse.python.cz](http://naucse.python.cz/2018/pyknihovny-jaro/fast-track/install/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/fast-track/install/).

Výukové materiály o requests:
[naucse.python.cz](http://naucse.python.cz/2017/pyknihovny-jaro/intro/requests/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/intro/requests).

Výukové materiály o clicku:
[naucse.python.cz](http://naucse.python.cz/2017/pyknihovny-jaro/intro/click/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/intro/click).

Úkol
----

Vaším úkolem je vytvořit aplikaci `starrer.py`, která bude spravovat hvězdičky
u repozitářů na GitHubu.
Podpříkaz `add` přidá hvězdičku:

```console
$ python starrer.py add pyvec/naucse.python.cz
```

Podpříkaz `remove` hvězdičku odebere:

```console
$ python starrer.py remove pyvec/naucse.python.cz
```

Podpříkaz `show` vypíše jméno repozitáře s hvězdičkou nebo bez hvězdičky podle
toho, jestli u něj vaše hvězdička je nebo ne:

```console
$ python starrer.py show pyvec/naucse.python.cz encukou/naucse.python.cz pyladiescz/pyladies.cz
* pyvec/naucse.python.cz
  encukou/naucse.python.cz
* pyladiescz/pyladies.cz
```

Program samotný i podpříkazy musí vypsat nápovědu pomocí přepínače `--help`.

Přihlašovací údaje se budou načítat ze souboru `auth.cfg` ve formátu
[INI](https://en.wikipedia.org/wiki/INI_file)
(použijte [ConfigParser](https://docs.python.org/3/library/configparser.html) –
viz sekce „Chraňte své tokeny“ v lekci o Requests).

Řešení dejte do Gitu a nahrajte na GitHub.

Budete-li mít k úkolu nějakou otázku, nebo budete-li ho chtít zkontrolovat,
ptejte se prosím na Slacku!


## Bonusy

### Volitelný konfigurační soubor

Bez ohledu na zvolený příkaz se cesta ke konfiguračnímu souboru zadává
nepovinným přepínačem (option) `-c`/`--config`. Pokud není specifikován,
bere se výchozí cesta `./auth.cfg` (avšak ani tento soubor nemusí existovat).

### „Ukecaný“ mód

Pokud uživatel zadá přepínač `-v`/`--verbose`, program bude zobrazovat
URL, na které přistupuje a HTTP metody. Například:

```console
$ python starrer.py add -v pyvec/naucse.python.cz
PUT https://api.github.com/user/starred/pyvec/naucse.python.cz
```

Tuto informaci vypisujte na *chybový* výstup, `sys.stderr`:

```python
import sys
print('Tohle se ukáže na chybovém výstupu', file=sys.stderr)
```

### Všechny repozitáře

Přepínač `--all-my` pro `starrer.py show` zajistí, že příkaz vypíše všechny
repozitáře přihlášeného uživatele.
Pokud je některý z nich *fork* (kopie jiného repozitáře), ukáže se informace
pro „rodičovský“ repozitář.


## Úkoly pro pokročilé

Nestačí-li vám to, zkuste úkoly, které jsme pro tuto lekci zadali studentům
magisterského studia na ČVUT.
Úkoly byly pro každý semestr jiné:

1. https://github.com/cvut/MI-PYT/blob/b161/tutorials/01_requests_click.md#%C3%9Akol
2. https://github.com/cvut/MI-PYT/blob/b171/tutorials/01_requests_click.md#%C3%9Akol
