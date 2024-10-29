# Tisk na konzoli
Jednoduché prosté a elegantní:
``` Python	
print("Hello World!")
```

## Barevný výstup
Přidání barevného výstupu:
``` Python
# Reset
Color_Off='\033[0m'       # Text Reset
NC='\033[0m'              # No Color

# Regular Colors
Black='\033[0;30m'        # Black
Red='\033[0;31m'          # Red
Green='\033[0;32m'        # Green
Yellow='\033[0;33m'       # Yellow
Blue='\033[0;34m'         # Blue
Purple='\033[0;35m'       # Purple
Cyan='\033[0;36m'         # Cyan
White='\033[0;37m'        # White

print("Calculating ... ")
print(Green + "Done" + NC)
```

> [!Note]
> Určitě se ptáte: Co je to za šílené změti písmen a číse?
> Jde o takzvané: "**ANSI** escape kódy". Je to historický přežitek z doby prvních počítačových terminálů a slouží pro základní formátování textu a změnu barvy. Jsou šílené, protože v tehdejší době byli počítače pomalé a každý přenesený Bajt po seriové lince se počítal. Jsou však užitené, protože umožňují jednoduché obarvení textu a fungují prakticky na všech počítačích.
> Více nám prozradí [wiki](https://cs.wikipedia.org/wiki/ANSI_escape_kód). 

## Cvičení:
- [Tiskneme do konzole](../notebooks/tiskneme%20do%20konzole.ipynb)

## Dále:
- [proměnné](./proměnné.md)