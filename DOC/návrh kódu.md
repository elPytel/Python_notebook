# Návrh kódu

Při programování obecně teorie rozlišuje dva přístupy:
- [zdola nahoru](./návrh%20kódu.md#zdola-nahoru),
- [shora dolů](./návrh%20kódu.md#shora-dolů).

## Zdola nahoru
Tento přístup je vhodný pro menší projekty, nebo když nevíme co všechno bude potřeba. Umožnuje nám napsat jednu funkci, tu vyladit a dobře ozkoušet. Člověk si tak nejdříve připraví malé bloky podobě, jako například kostičky lego (malé, každá jiná) a znich až poté staví větší kusy programu. 

Nevíhodou může být že je těžší dělit práci mezi více programátorů (nashodli se na tom jak spolu budou části programu komunikovat).

```Python
def print_player_score(player_name, score, time_in_game, is_winer):
    print(f"Player {player_name} has score {score} in time {time_in_game}.")
    if is_winer:
        print(f"Player {player_name} is winer.")
    else:
        print(f"Player {player_name} is looser.")

if __name__ == "__main__":
    player_name = "John"
    score = 100
    time_in_game = 1000
    is_winer = True

    print_player_score(player_name, score, time_in_game, is_winer)
```

### K čemu je toto dobré?

Už umíme vytisknout skóre hráče, což je nedílná součást našeho programu, lehce jsme otestovali že funkce dělá co má. 
Ale co vůbec nevíme jak tento kód zapojit do zbytku programu. To ukáže až čas a hromada zdravé refaktorizace kódu.

## Shora dolů
Tento přístup je vhodný pro větší projekty, kde je potřeba rozdělit kód na menší části. Výhodou je, že je kód přehlednější a snadněji se ladí. Nevýhodou je, že je potřeba vědět co všechno bude potřeba a jak to bude fungovat.

```Python
class Game:
    def __init__(self, players):
        self.players = players
        pass

    def eval(self):
        pass

    def is_valid_move(self, move):
        return True

    def is_game_over(self):
        for player in self.players:
            if not player.is_alive():
                return True

    def print_score(self):
        pass

class Player:
    def __init__(self):
        pass

    def next_move(self):
        pass

    def is_alive(self):
        return True

if __name__ == "__main__":
    # inicializace hry
    player = Player()
    game = Game([player])

    # beh hry
    while not game.is_game_over():
        # tah hrace
        move = player.next_move
        # ceka se na validni tah
        while not game.is_valid_move(move):
            move = player.next_move
        # vyhodnoceni tahu
        game.eval(move)

    # konec hry
    game.print_score()
```

Máme přehled o třídách, funkcích a nějakých proměnných. 

> [!note]
> Dáváme do funkcí výraz `pass`, který dává najevo, že funkce zatím nic sice nedělá a ještě se k ní plánujeme vrátit. Pokud by byli funkce úplně prázdné, tak by nás kontrola syntaxe nebo interpretor dost nevybíravě informoval o tom, že nám v programu něco chybí.
### Rozdělení na menší části
Můžeme extrahovat objekty do vlastních modulů (knihoven). Získáme tak menší zdrojové soubory, ve kterých by se nám mělo snadněji orientovat. 

```Python
import Game
import Player

if __name__ == "__main__":
    # inicializace hry
    player = Player.Player()
    game = Game.Game([player])

    # beh hry
    while not game.is_game_over():
        # tah hrace
        move = player.next_move
        # ceka se na validni tah
        while not game.is_valid_move(move):
            move = player.next_move
        # vyhodnoceni tahu
        game.eval(move)

    # konec hry
    game.print_score()
```

### K čemu je toto dobré?

#### Více implementací stejného
Já mohu: 
1. specifikovat `interface` - funkce jednotlivých objektů. 
2. napsat si vlastní soubor `Game.py`.
3. Rozeslat původní prázdnou implementaci kolegům programátorům a každý z nich mi může vráti svojí vlastní implementaci hráče: `Player.py`.

Pak můžeme poměřit své programátorské schopnosti a nechat hrát různé hráče/boty proti sobě.

#### Rozdělení práce
1. specifikace `interface` - funkce jednotlivých objektů. 
2. Každý z programátorů z týmu dostane na starost vlastní část programo.
3. Výsladná aplikace se složí z těchto menších celků.

#### Testování
Můžeme testovat jednotlivé části programu zvlášť. Každý z programátorů může testovat svoji část programu (modul, balíček, funkci) a nemusí čekat na ostatní.

## Závěr

V praxi se používá něco mezi, ale je dobré vědět že tyto přístupy existují. 