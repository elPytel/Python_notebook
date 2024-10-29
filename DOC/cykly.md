# Cykly
Základní cykly (smyčky) pro vykonávaní kódu jsou:
- for, 
- foreach,
- while, 
- do-while.

> [!note]
Všechny jsou však ekvivalentní, tj. každý cyklus `for` lze přepsat na cyklus `while` a naopak. 

Python má však implementovány pouze cykly `for` a `while`. 

## Cyklus `for`
``` Python
for i in range(10):
    print(i)
```

### Funkce `range()`
Funkce `range()` vrací sekvenci čísel od 0 do zadaného čísla. 

Plný počet argumentů:
``` Python	
range(start, stop, step)
```

## Cyklus `while`
``` Python
i = 0
while i < 10:
    print(i)
    i += 1
```

Cykli lze také řídit pomocí klíčových slov:
- continue - přeskoč,
- break - ukonči cyklus.

## Cvičení:
- [Cykly](../notebooks/cykly.ipynb)

### Dále:
- [funkce](./funkce.md)