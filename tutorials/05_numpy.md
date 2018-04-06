
NumPy
=====

Výukové materiály:
[naucse.python.cz](http://naucse.python.cz/2018/pyknihovny-jaro/intro/numpy/).

Stáhněte si soubor [generator.py](05-numpy/generator.py).
V něm je funkce `maze`, která vytváří NumPy matici s bludištěm.
Vyzkoušejte si ji v Notebooku:

```python
from matplotlib import pyplot
%matplotlib inline

import generator  # předpokládá že `generator.py` je ve stejném adresáři jako notebook

maze = generator.create_maze()

pyplot.imshow(maze)
```

Jak tohle bludiště vypadá jako matice čísel?

```python
maze
```

---

Vaším úkolem je vytvořit funkci `analyze(array)`, která bude hledat cestu bludištěm.

Na vstupu bude bludiště uložené v matici, kde:

* záporné honoty představují zeď (kterou nejde projít)
* nezáporné hodnoty předstvaují průchozí prostor
* 1 představuje cíl (ten je jen jeden, ale můžete to napsat i tak, aby jich mohlo být víc)

V bludišti se lze pohybovat pouze horizontálně nebo veritkálně. Hranice matice jsou neprůchozí.

Funkce vrátí matici, kde pro každé políčko, ze kterého se dá dostat do cíle, bude délka nejkratší cesty k cíli, jinak -1. (Pro cíl tedy v téhle matici bude 0, pro zdi `-1`, pro nedostupná políčka `-1`).

Bonus: Zkus zařídit, aby program fungoval i pro jiné druhy bludišť než ty co
generuje funkce `create_maze`.
Třeba bludiště se slepými uličkami, bez zdi u okrajů, nebo s tlustšími cestičkami.
