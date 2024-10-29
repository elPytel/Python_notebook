# Instalování balíčků (knihoven)
Instalace knihoven se provádí pomocí nástroje [pip](https://pip.pypa.io/en/stable/).

## Instalace knihovny v příkazovém řádku
```Bash
python -m pip install <nazev_knihovny>
```

## Něco více o knihovnách

### `time`
Jednou ze základních knihoven na kterou by mohl člověk narazit je knihovna `time`, tedy čas.

```Bash
python -m pip install time
```

```Python
import time # importovani khihovny do programu

def main():
    print("Calculating ... ")
    time.sleep(7)  # uspani programu na 7 sekundu
    print("Still calculating ... ")
    time.sleep(5)
    print("Almost done ... ")
    time.sleep(1)
    print("Done")
    pritn("Your result is: 42")
    
main()
```

### `math`
### `random`
### `matplotlib`