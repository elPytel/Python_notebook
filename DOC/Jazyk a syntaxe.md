
## Jazyk a syntaxe
``` Python
# jednoradkovy komentar

"""
Vice-radkovy
komentar
"""
```

### Můj první program
Je ustáleným zvykem pojmenovávat hlavní soubor programu nebo spouštěnou funkci `main`. Proto začnětě vytvořením souboru `main.py`. Přípona `.py` odkazuje na Python a uvádí, že jde o soubor se zdrojovým kódem skryptovacího (programovacího) jazyka Python.
``` Python
# muj prvni program
def main():
    print("muj prvni program")
main()
```

### Tisk na konzoli
Přidání barevného výstupu:
``` Python
# Reset
Color_Off='\033[0m'       # Text Reset
NC='\033[0m'

# Regular Colors
Black='\033[0;30m'        # Black
Red='\033[0;31m'          # Red
Green='\033[0;32m'        # Green
Yellow='\033[0;33m'       # Yellow
Blue='\033[0;34m'         # Blue
Purple='\033[0;35m'       # Purple
Cyan='\033[0;36m'         # Cyan
White='\033[0;37m'        # White

print("Calculating ..." + Green + "Done" + NC)
```

Cvičení:
- [Tiskneme do konzole](../notebooks/tiskneme%20do%20konzole.ipynb)