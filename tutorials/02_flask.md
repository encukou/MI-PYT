
Webové aplikace: Flask
======================

Výukové materiály o Flasku:
[naucse.python.cz](http://naucse.python.cz/2018/pyknihovny-jaro/intro/flask/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/intro/flask).

Výukové materiály o deploymentu:
[naucse.python.cz](http://naucse.python.cz/2018/pyknihovny-jaro/intro/deployment/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/intro/deployment).

Výukové materiály o PythonAnywhere:
[naucse.python.cz](http://naucse.python.cz/2018/pyknihovny-jaro/intro/deployment/pythonanywhere/),
[GitHub](https://github.com/pyvec/naucse.python.cz/tree/master/lessons/intro/deployment).

Úkol
----

Tvým úkolem je naprogramovat webovou službu, která bude automaticky
reagovat na komentáře na GitHubu.

Jak takovou reakci přidat se dozvíš v [dokumentaci](https://developer.github.com/v3/reactions/).
Pozor na to, že toto API ještě není úplně doladěné;
je zatím potřeba přidat do hlavičky `Accept` dát speciální hodnotu
`application/vnd.github.squirrel-girl-preview+json`.

Založ si repozitář, kde budeš podobné věci zkoušet, v něm v záložce
*issues* nahlaš fiktivní chybu a přidejte pár komentářů.

Pozor na to, že GitHub odlišuje "reactions for an issue comment", reakce na
opravdové komentáře,
a "reaction for an issue", reakci na popisek který na webu vypadá jako
první komentář.
Po kliknutí na čas u komentáře se ti v prohlížeči v URL objeví číselné `id`
konkrétního příspěvku, který pak můžete použít v API.
Pro popisek použijte číslo samotné *issue*.

Zkus si reagovat na komentáře pomocí Requests.
Potřebná data předáš pomocí argumentu `json`, např. následující kód
přidá smajlíka k [popisku mé testovací *issue*](https://github.com/encukou/test-repo/issues/1):

```python
response = session.post(
    'https://api.github.com/repos/encukou/test-repo/issues/1/reactions',
    headers={'Accept': 'application/vnd.github.squirrel-girl-preview+jso'},
    json={'content': 'laugh'}
)
response.raise_for_status()
```

Potom vytvoř pomocí `flask` webovou službu, která bude po navštívení určitých
URL rozdávat reakce ve tvém (či mém) testovacím repozitáři.

Program si nech zkontrolovat od kouče, jestli v něm není bezpečnostní chyba,
a nasaď na PythonAnywhere.


## Bonus 1: Formulář

Umíš-li v HTML dělat formuláře, nastuduj si jak se ve Flasku
zpracovává [metoda POST](http://flask.pocoo.org/docs/0.12/quickstart/#http-methods)
a [data z formuláře](http://flask.pocoo.org/docs/0.12/quickstart/#the-request-object).
Pak udělej na přiřazování reakcí formulář.


## Bonus 2: Webhook

GitHub umí takzvané *webhooks*: když si to v repozitáři nastavíš,
po určitých akcích – například když někdo přidá komentář – GitHub
automaticky navštíví danou URL a pošle spoustu
informací.
Všechno je to popsáno v [dokumentaci](https://developer.github.com/webhooks/).

Webhook se přidá ze *Settings* u repozitáře, v sekci Webhooks.
Zkus si nějaký webhook přidat pro URL `https://example.com/` a volbu
*Send me everything*.
Pak přidej v repozitář komentář.
Zpátky v sekci Webhooks si rozklikni záznam webhooku a v *Recent Deliveries*
si rozklikni informace, které Github poslal.

Zkus udělat server, který na každý nový komentář s textem `Jupí!`
zareaguje smajlíkem.

Pozor na to, že adresy jako `localhost`, `0.0.0.0`, `127.0.0.1` fungují jen
z tvého počítače. GitHub se k nim nedostane.
Než tedy začneš webhook používat, musíš službu nasadit.

Do té doby si svoji službu můžeš lokálně (na svém počítači) otestovat pomocí
Requests: pomocí `json` posílej taková data, která by poslal GitHub.

Ve Flasku se k poslaným informacím dostaneš pomocí
[`request.get_json()`](http://flask.pocoo.org/docs/0.12/api/#flask.Request.get_json):

```python
from flask import request

...

request.get_json()
```


## Úkoly pro pokročilé

Nestačí-li vám to, zkuste úkoly, které jsme pro tuto lekci zadali studentům
magisterského studia na ČVUT.
Úkoly byly pro každý semestr jiné a navazovaly na úkoly předchozí:

1. https://github.com/cvut/MI-PYT/blob/b161/tutorials/02_flask.md#%C3%9Akol
2. https://github.com/cvut/MI-PYT/blob/b171/tutorials/02_flask.md#%C3%9Akol
