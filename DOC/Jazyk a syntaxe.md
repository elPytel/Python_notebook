# Jazyk a syntaxe

## Ozubená kolečka někdě uvnitř

> [!tip]
> Nutné zlo: syntaxe. Syntaxe je soubor pravidel, které určují jakým způsobem se píše kód v daném programovacím jazyce. Syntaxe je tedy jakýsi jazyk, kterým se programátor domlouvá s počítačem.

### Python a jeho interpretr
Python je interpretovaný jazyk. To znamená, že se kód vykonává postupně řádek po řádku. Výhodou je, že se kód může spouštět bez kompilace, což znamená, že se nemusí překládat do strojového kódu. Nevýhodou je, že je pomalejší než kompilované jazyky.

U jiných jayzků, jako je C, C++, Java, se kód nejprve přeloží do strojového kódu a až poté se spustí. Při kompilaci se tak zjištují chyby, které by mohly nastat při běhu programu. Probíhá optimlizace kódu a jeho zrychlení. To jsou věci na které Python trochu trpí.

## Můj první komentář
Komentář se značí: `#` - hash-tag. Veškerý text na řádku uvedený za ním se nevykoná, ale je pouze pro programátora.

``` Python
# jednoradkovy komentar

"""
Vice-radkovy
komentar
"""
```

## Můj první program
Je ustáleným zvykem pojmenovávat hlavní soubor programu nebo spouštěnou funkci `main`. Proto začnětě vytvořením souboru `main.py`. Přípona `.py` odkazuje na Python a uvádí, že jde o soubor se zdrojovým kódem skryptovacího (programovacího) jazyka Python.

``` Python
# muj prvni program
def main():
    print("Muj prvni program.")
main()
```

### Dále:
- [tiskneme do konzole](./Tisk%20na%20konzoli.md)