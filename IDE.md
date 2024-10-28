## IDE
Vývojové prostředí (zkratka IDE, anglicky integrated development environment) je software usnadňující práci programátorů.

### Online
Plně dostačující vývojové prostředí v prohlížeči. Umožnuje vytvářet: 
- jednotlivé projekty
- sdílet hotové programy
- kooperovat v reálném čase při psaní jednoho programu.

Stránka: [replit.com](https://replit.com/)

### Offline
#### Interpreter jazyka
Slouží pro spuštění programu. Kód spouští - "interpretuje" řádek po řádku. Lze jej stáhnout z oficiálních stránek, 
nebo například přímo v M$ store:
- [python.org](https://www.python.org/downloads/)
- [M$ store](https://www.microsoft.com/store/productid/9NRWMJP3717K?ocid=pdpshare)

#### IDE
Pokud nechcete psát programy v poznámkovém bloku, tak je vhodné si na počítač stáhnout IDE. 
Mezi velmi populární varianty patří například:
- [VS Code](https://code.visualstudio.com/)
- [pycharm](https://www.jetbrains.com/pycharm)

## VS Code 
Je prostředí od Micro$oftu. Je velmi jednoduché a veškeré další funkcionality se do něj získavají pomocí rozšíření. 
 
### Rozšíření
Ty se instalují přímo ve VS Code v záložce vlevo na svislé liště (ikona tetrisu).
Doporučená rozšíření:
- Python (Micro$oft)

## Instalování balíčků (knihoven)
Instalce knihoven se provádí pomocí nástroje [pip](https://pip.pypa.io/en/stable/).

### Nečo více o knihovnách

#### `Time`
Jednou ze základních knihoven na kterou by mohl člověk narazit je knihovna Time, tedy čas.

```Python
import time # importovani khihovny do programu

def main():
    print("something")
    time.sleep(1)  # uspani programu na 1 sekundu
    print("something2")
    
main()
```