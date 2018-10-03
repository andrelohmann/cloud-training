# Tools installation

Installation aller benötigten Tools

## terminator

terminator ist ein multiple window terminal

```
sudo install terminator
```

### Shortcuts

| Shortcut                  | Ergebnis                                                |
|---------------------------|---------------------------------------------------------|
| Ctrl + Shift + O          | Terminal-Fenster horizontal teilen                      |
| Ctrl + Shift + E          | Terminal-Fenster vertikal teilen                        |
| Ctrl + Shift + W          | Aktuellen Terminal schließen                            |
| Alt + Right               | Zum rechten Terminal wechseln                           |
| Alt + Left                | Zum linken Terminal wechseln                            |
| Alt + Up                  | Zum oberen Terminal wechseln                            |
| Alt + Down                | Zum unteren Terminal wechseln                           |
| Ctrl + Shift + X          | Ansicht wechseln zwischen allen und aktuellem Terminal  |
| Left Alt + A              | Alle Terminals gruppieren                               |
| Left Alt + G              | Gruppierung aufheben                                    |

### Infinite Scroll

Für ein endloses zurück scrollen innerhalb des Terminator Fensters ist die Datei ~/.config/terminator/config zu bearbeiten.

```
nano ~/.config/terminator/config
```

```
...
[profiles]
  [[default]]
    scrollback_infinite = True
```

## git

distributed revision control system

```
sudo install git
```

## python virtualenv

```
sudo install git
```

## network tools

```
sudo install nmap tcptraceroute
```

## atom

```
sudo install atom
```

## virtualbox

```
sudo install virtualbox
```

## SSH Key

```
ssh-keygen
```
