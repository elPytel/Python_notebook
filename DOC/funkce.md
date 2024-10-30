# Funkce

Jak se vytváří funkce v Pythonu?
``` Python
def absolutni_hodnota(cislo):
    """
    Funkce vrati absolutni hodnotu zadaneho cisla.
    """
    return cislo if cislo >= 0 else -cislo
```

Klauzule `def` je klíčové slovo, které říká že se jedná o definici funkce. Následuje jméno funkce *absolutni_hodnota* a závorky s parametry *cislo*. Tělo funkce je odsazené o 4 mezery nebo tabulátor. 

Víceřádkový komentář v těle funkce je tzv. **docstring**, který popisuje co funkce dělá a je znakem dobrého stylu programování.

Jak se funkce volá?
``` Python
print(absolutni_hodnota(-5))
```

Funkce také lze volat s pojmenovanými argumenty:
``` Python
print(absolutni_hodnota(cislo=-5))
```

## Požadavky na funkci
Funkce by měla ideálně:
- dělat jednu věc,
- být krátká.

> [!tip]
> Dalším dobrým doporučením je parametrizovat vše co jde. Tedy pokud něco jde předat funkci argumentem, tak to udělejte!

``` Python
def tisk_domecek():
    print("   *   ")
    print("  ***  ")
    print(" ***** ")
    print("*******")
    print("*******")
    print("*******")
    print("*******")
```

Není dobrá funkce, protože dělá více věcí. Měla by být proto rozdělena na více funkcí.

``` Python
def tisk_trojuhelnik():
    print("   *   ")
    print("  ***  ")
    print(" ***** ")
    print("*******")

def tisk_obdelnik():
    print("*******")
    print("*******")
    print("*******")
    print("*******")

def tisk_domecek():
    tisk_trojuhelnik()
    tisk_obdelnik()
```

Je sice lepší zápis ale naše dílčí funkce nejsou vůbec parametrizované. Pojďme to tedy změnit.

``` Python
def tisk_trojuhelnik(charakter, vyska):
    for i in range(vyska):
        mezery = " " * (vyska - i - 1)
        znaky = charakter * (2 * i + 1)
        print(mezery + znaky)
        
def tisk_obdelnik(charakter, sirka, vyska):
    for i in range(vyska):
        print(charakter * sirka)

def tisk_domecek(charakter, vyska, sirka):
    tisk_trojuhelnik(charakter, vyska)
    tisk_obdelnik(charakter, sirka, vyska)
```

Nyní máme funkce, které jsou parametrizované a každá z nich dělá jednu věc.

> [!note]
> Zápis `charakter * sirka` vytvoří řetězec, který má `sirka` znaků `charakter`.

## Kdy má člověk vytvořit funkci?
- **Spagety code** - kód je nečitelný (příliš mnoho vnoření, složité podmínky),
- Opakující se kus kódu (programuji ctrl+c, ctrl+v).

Krátké video na YouTube: [Why You Shouldn't Nest Your Code](https://www.youtube.com/watch?v=CFRhGnuXG-4&t=12s)

### Vnoření kódu
Uvádí se že kód, který má více jak tři vnoření je kandidátem na refaktorizaci. To znamená že by měl být rozdělen na více funkcí, které budou mít jasně daný úkol.

``` Python
def main():
    charakter = "*"

    pocet_obdelniku = 4
    sirka = 5
    vyska = 3

    for i in range(pocet_obdelniku):
        for j in range(vyska):
            for k in range(sirka):
                print(charakter, end="")
            print()
        print()

if __name__ == "__main__":
    main()
```

Maximální vnoření v tomto kódu je 4.

Nabízí s se tak extrahovat vnořené cykly do samostatné funkce.

``` Python
def tisk_linky(charakter, delka):
    for _ in range(delka):
        print(charakter, end="")
    print()

def tisk_obdelniku(charakter, sirka, vyska):
    for _ in range(vyska):
        tisk_linky(charakter, sirka)
    print()

def main():
    charakter = "*"

    pocet_obdelniku = 4
    sirka = 5
    vyska = 3

    for i in range(pocet_obdelniku):
        tisk_obdelniku(charakter, sirka, vyska)

if __name__ == "__main__":
    main()
```

Kód je pak přehldenější a funkci `tisk_obdelniku` můžeme použít i jinde v programu.

## Cvičení:
- [Funkce](../notebooks/funkce.ipynb)

## Dále:
- [Práce se soubory](./práce%20se%20soubory.md)
