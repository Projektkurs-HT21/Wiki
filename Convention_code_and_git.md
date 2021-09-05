# Konventioner för kod och Git
Här är lite konventioner för hur man skriver kod och använder Git. Då vi är femton personer som skriver på samma dokument och använder samma repon, är det viktigt att alla följer dessa.

## Kommentarer på kod
Kod ska inte kommenteras för mycket. Det betyder att varje rad av en funktion eller liknande inte behöver en egen kommentar för vad den gör. Behöver den det bör du skriva bättre kod. Variabel- och funktionsnamn bör vara nog tydliga för att man ska förstå dess funktion.

För att dokumentera vad en funktion gör, utöver dess namn, kan en kommentar över funktionen användas.

Exempel på en bra kommenterad funktion

```python
# A function for those of you who dont know what to do. Takes an input, 
# increments and returns a boolean
def i_dont_know_what_im_doing(some_var):
    some_var += 1
    if some_var > 5:
        return False

    return True
```

Här är ett tydligt funktionsnamn, med en kommentar ovanför som beskriver vad den gör.

Exempel på en dåligt kommenterad funktion.

```python
def dont_know_func(var):    # A function that dont knows
    var += 1                # Increments var
    if var > 5:             # Check the size of var and returns false if it is bigger than five
        return False

    return True
```

Här är funktionsnamnet och variabelnamnet dåligt beskrivande. Varje rad har en kommentar som beskriver vad raden gör trots att det är ganska tydligt när man tittar på koden. Det resulterar i alldeles för mycket kommentarer.

## Commit messenges
Sammanfattningen av en commit, dvs ett commit messenge, ska vara kort och beskrivande. För att underlätta för Jan ska commit messenges vara på engelska, och de ska också beskriva _vad som är skillnaden från föregående commit_ och inte _vad du gjort_.

Exempel på ett bra commit messenge.

```
Add this function to this thing
```

Här beskrivs kort om vad som är skillnaden från förra versionen; att något lagts till.

Exempel på ett dåligt commit messenge.

```
Added this function and did some other stuff. Made some comments and moved a function two lines up.
```

Här beskrivs vad du personligen har gjort. Det är för mycket text och en hel del av det är inte väsentligt för att få en översikt över projektets olika versioner.

## Branches
Det viktigaste är att ni inte pushar till main branchen. Det gäller alla repositories. Gör en ny branch eller checkouta till en existerande, committa dina ändringar och gör ett pull request till mainbranchen. Om du inte vet hur det fungerar, fråga din gruppledare eller den som är ansvarig för Git i gruppen.

Den som är ansvarig för Git i gruppen har i uppgift att acceptera pull requests; för era egna repositories får ni merga in i main, och i de delade repositories får ni merga in i gruppens branches.
