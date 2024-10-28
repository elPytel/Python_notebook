
## Programujeme v Pythonu

### Proměnné 
> Pojmenování věcí je to vůbec nejtěžší na programování.

Dobrý nápad je většinou pojmenovávat věci tak aby z jejich názvu bylo jasné co mají obsahovat.
Co když bude název několika slovný?
To vůbec není problém, protože žijeme v době IDE plných:
- našeptávačů a automatického doplňování,
- a hromadné přejmenování je také opravdu mocný nástroj.


![now only god knows how this code works](https://pbs.twimg.com/media/CpIUd8jXYAAtkvE.jpg)

Ideální stav pojmenovávání je takový, že dojdeme do stavu kdy není potřeba psát komentář k tomu aby jsme věděli co program vykonává (a to i po půl roce co jsme ho neviděli).

![spagety code](https://miro.medium.com/v2/1*NT1um6PYhJU4q9E26cQUew.png)

> Čistý kód se pozná tak, že jej můžete číst jako prózu.

Kód s dobrými názvy proměnných, tříd, funkcí... se stává samo popisným (obzvláště v Pythonu), stačí ho tedy přečíst jako větu, která nám dá sama o sobě dostatečně dobrou představu o tom co program vykonává.

Najaká užitečná videa:
- [Naming Things in Code](https://www.youtube.com/watch?v=-J3wNP6u5YU&t=116s)
- [Don't Write Comments](https://www.youtube.com/watch?v=Bf7vDBBOBUA)

### Funkce
Kdy má člověk vytvořit funkci?
- Spagety code - kód je nečitelný (příliš mnoho vnoření)
- Opakující se kus kódu (programuji ctrl+c, ctrl+v)

Krátké video na YouTube: [Why You Shouldn't Nest Your Code](https://www.youtube.com/watch?v=CFRhGnuXG-4&t=12s)

### OOP
K čemu je objektové programování?

Programování jde z hlediska přístupu rodělit na:
- Funkcionální programování,
- Objketově orientované.

Zástupcem funkcionálního programování může být například [Lisp](https://cs.wikipedia.org/wiki/Lisp) a ojektového [Java](https://cs.wikipedia.org/wiki/Java_(programovací_jazyk)).

Když se člověk dostatečně podrobně seznámí s proměnnými, poli a dalšími datovými typy tak jsou na řadě "struktury". Ty nám umožnují ukládat spolu data, která k sobě patří. Může si to představit jako záznam nějakého typu. Jako příklad si uvedeme kartotéku. Můžeme si o lidech ukládat například: **jméno**, **věk**, **pohlaví**, **místo_narození**, **zaměstnání**.

Zde je příklad jednoho záznamu v podobě slovníku:
``` Python
osoba = {
    "jméno": "Pepa",
    "věk": 30,
    "pohlaví": "muž",
    "místo_narození": "Praha",
    "zaměstnání": "elektrikář"
}
```

Kartotéka která uchovává pouze jeden záznam není moc užitečná. Nejspíše by jsme chtěli ukládat záznamy rovnou o několika různých lidech. Co s tím? Může si vytvořit pole (v Pythonu list) pro každá atribut našeho záznamu. Jak budeme lidi přidávat do kartotéky, tak se postupně naše seznamy prodlužují.

``` Python
# Seznamy s informacemi o jednotlivých osobách
jmena = ["Pepa", "Marie", "Jakub"]
veky = [30, 25, 35]
pohlavi = ["muž", "žena", "muž"]
mista_narozeni = ["Praha", "Brno", "Ostrava"]
zamestnani = ["elektrikář", "učitelka", "lékař"]
```

Data takto vskutku v programu ukládat lze, není to příliš pohodlné. Zamyslete se by bylo potřeba udělat v případě:
- přidání nového člověka (to není zas tak těžké),
- odstranění `Pepy` z naší kartotéky,
- změnění zaměstnání `Marie`,
- vypsání všech záznamů, se všemi atributy, seřazených abecedně podle jména,
- přidání atributu `místo_byliště` u nových záznamů.

Některé ulohy by nebyli zas tak težké, nad jinými by se zapoťil i dobrý programátor.

Nebo by jsme mohli vzít náš původní slovník a vložit jej do pole a podle potřeby přidávat další zázamy lidí. To není o nic horší přístup, ale nakonec si moc nepomůžeme!

Zde je dobré šáhnout práve po struktuře (Python narozdíl od jazyků jako například C nerozlišuje struktury a oběkty). Jednoduchá třída reprezentující člověka pak může vypadat takto:
``` Python
class Clovek:
    def __init__(self, jmeno, vek, pohlavi, misto_narozeni, zamestnani):
        self.jmeno = jmeno
        self.vek = vek
        self.pohlavi = pohlavi
        self.misto_narozeni = misto_narozeni
        self.zamestnani = zamestnani
```

Vytvoření `instance` záznamu našeho Pepy:
``` Python
# Vytvoření instance bez názvů atributů
pepa = Clovek("Pepa", 30, "muž", "Praha", "elektrikář")
```

Nyní když budeme chtít přidat další lidi do katotéky, tak použijem list instancí objektu člověk:
``` Python
# Vytvoření pole lidí "kartoteka" a přidání záznamů
kartoteka = []

pepa = Clovek("Pepa", 30, "muž", "Praha", "inženýr")
marie = Clovek("Marie", 25, "žena", "Brno", "učitelka")
jakub = Clovek("Jakub", 35, "muž", "Ostrava", "lékař")

kartoteka.append(pepa)
kartoteka.append(marie)
kartoteka.append(jakub)
```

Není bude hledání a práce s našimi uloženými daty o poznání jednodušší. Při procházená kartotékou si většinou vystačíme s jedním cyklem a u aktuálního člověka budeme mít rovnou přístupné všechny jeho atributy. Například když budeme chtít seřadit všchny lidi abecend včetně jejich stributů, tak můžem použít metodu `.sort`:

``` Python
# Seřazení kartotéky podle jména abecedně
kartoteka.sort(key=lambda x: x.jmeno)
```
Využívá se zde lambda funkce, tím si zatím nemusíme nikterakt komplikovat život. Stačí vědět že je to způsob jak říci metodě `.sort` podlě čeho má pole setřídit. Pokud by jsme chtěli lidi seřadit podle věku, tak by se to dalo udělat obdobně bez jakýhkoliv obtíží.

Jak by nám řekli v teleshopingu:
> Ale to není vše!
- Horst Fuchs 

Objektové programování má mnohem více triků ve svém rukávu. Spojení dat do spolu souvisí k sobě programátorům nestačilo, a tak přidali k objektům ještě vlastnosti `funkce`, díky nimž v sobě neukládají data, ale můžou se i nějak chovat.

Ukážeme si trochu větší program, který by se dal využít v matematické knihovně:
``` Python
import math

class Shape:
    def obvod(self):
        pass
    
    def plocha(self):
        pass

class Trojuhelnik(Shape):
    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c
    
    def obvod(self):
        return self.a + self.b + self.c
    
    def plocha(self):
        s = self.obvod() / 2
        return math.sqrt(s * (s - self.a) * (s - self.b) * (s - self.c))

class Obdelnik(Shape):
    def __init__(self, a, b):
        self.a = a
        self.b = b
    
    def obvod(self):
        return 2 * (self.a + self.b)
    
    def plocha(self):
        return self.a * self.b

class Kruh(Shape):
    def __init__(self, polomer):
        self.polomer = polomer
    
    def obvod(self):
        return 2 * math.pi * self.polomer
    
    def plocha(self):
        return math.pi * self.polomer ** 2

# Pole tvarů
tvary = [Trojuhelnik(3, 4, 5), Obdelnik(3, 4), Kruh(5)]

# Výpočet obvodu a plochy pro každý tvar v poli tvary
for tvar in tvary:
    print("Obvod:", tvar.obvod())
    print("Plocha:", tvar.plocha())
    print()
```

Co se to tam všechno děje? Kromě toho že třída `Shape` má vlastní metody (které nic nedělají `pass`), tak se využívá i pokročilejších konceptů objektového programování:
- Dědičnost,
- Polymorfizmus.

Pojdě si program rozebrat postupně. Nejdřív vytváříme třídu `Shape`, slouží nám jako taková šablona pro to co budeme dále dělat. Má dvě metody:
- `obvod`,
- `plocha`.

Dále vytváříme třídy `Trojuhelnik`, `Obdelnik`, `Kruh`, které jsou potomky tvaru a díky tomu **dědí** určité vlastnosti. V tomto případě je to existence funkcí na výpočet obovdu a obsahu.
Každá z těchto tříd má vlastní specifické funkce:
- konstruktor (atribudy ze kterých se vytváří instace),
- `.obvod()` - která vypočte obovod daného tělesa podle správného vzorce, do kterého dosadí hodnoty, které byli uloženy při vytvoření,
- `.plocha()` - obdobně má funkci na výpočet plochy.

Dále se v kódu vytváří list do kterého se uložené různé instance ruzných typů objektů.

V jednom cyklu for lze vypočítat obvod a plochu všech těles. Všimněte si že to jdeto právě díky tomu, že dědí všechny objekty stejně pojmenované funkce od rodiče `Shape`!

### TDD - test driven development
Když se človek dostane do stavu, že má dobře pojmenované věci v programu, hluboká vnoření a opakující struktury rozpletené do přehledných funkcí, máme odelenou logiku programu od práce s konzolí a dalšími vstupy a výstupu, tak to ještě neznamená že je vše růžové a program funguje. 

Programátoři přišli s konceptem testování kódu. Je to z toho důvodu že na rozdíl od matematické logiky (a jazyku Prolog, který je ní postavený) nelze u programu dokázat zda funguje a je správný. Můžete si říci: "Vždyť jsem to vyzkoušel! Spustil jsem progam a on fungoval!", ale to nám zdaleka nestačí. Pro to, aby šlo o nějaké aplikaci říci, že je funkční, tak by jsme museli otestovat všechny možné varianty jednotlivých vstupů a jejich kombinace. To pro běžnou aplikaci je nepředstavitelné množství lidské práce. Proto si pomůžeme testováním. 

Pro jazyk Python existuje nástroj pytest.
```Bash
pip install pytest
```

Program nyní jednoduše spustíme příkazem:
```Bash
pytest
```
(Na window je možné že bude potřeba přidat aplikaci do cesty spustitelných aplikací, aby správně fungoval)

Chybu na win jde také obejít spouštěním pomocí:
```Bash
python -m pytest
```

Teď už jen naprogramovat naše testy.

Psát ke každé funkci ještě kód který ji otestuje? To musí být strašně moc práce!

Ano, a je to přesně 2x tolik práce při psaní kódu, ale asi 1/5x práce při zkoušení aplikace a 1/10x při hledání chyb. A to už stojí za to si s tím tu práci dát.

#### Píšeme testy
Tak jdeme na to!
Program `pytest` bude standardně hledat testy v adresáři, kde ho spustíme. Testy k našemu programu snadno pozná podle toho, že začínají slovem *test* a jsou obecně ve tvaru: **text_xxx.py**.

Program pytest tyto soubory prohledá a spustí každou funkci, která se jmenuje **test_xxx**.

Pojdme si vyzkoušet. Když spustíme pytest na prázdno (v adresáři je náš pythnový projekt, ale zatím žádné testy), tak dostaneme hlášku:
```Bash
C:\Users\jerry\Python> python -m pytest
=============== test session starts ================
platform win32 -- Python 3.11.8, pytest-8.1.1, pluggy-1.4.0
rootdir: C:\Users\jerry\Python
collected 0 items                                    

============== no tests ran in 0.02s ===============
```
Což je dobré a říká nám tak že nemá co dělat.

Předpokládejme, že máme jednoduchý kód, který chceme otestovat. Například máme modul `calculator.py` obsahující funkci pro sčítání:
```python
# calculator.py

def add(a, b):
    return a + b
```

Nyní vytvoříme testovací soubor `test_calculator.py`:
```python
# test_calculator.py

from calculator import add

def test_addition():
    assert add(2, 3) == 5

def test_addition_negative_numbers():
    assert add(-1, 1) == 0
```
Ve výše uvedeném kódu jsou dvě testovací funkce: `test_addition()` a `test_addition_negative_numbers()`. Každá z těchto funkcí obsahuje jeden testovací případ, který ověřuje správnost funkce `add()`.

```Bash
C:\Users\jerry\Python> python -m pytest
=============== test session starts ================
platform win32 -- Python 3.11.8, pytest-8.1.1, pluggy-1.4.0
rootdir: C:\Users\jerry\Python
collected 2 items

test_calculator.py ..                         [100%] 

================ 2 passed in 0.02s =================
```
Jak můžeme vidět, tak oba testovací případy prošly.

### Dále
- [Návrh kódu](./návrh%20kódu.md)