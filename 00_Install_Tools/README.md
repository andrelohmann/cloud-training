# Tools installation

Installation aller benötigten Tools

## terminator

terminator ist ein multiple window terminal

```
sudo apt-get install terminator
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
sudo apt-get install git
```

Nachdem git installiert wurde, bietet es sich sich, ein paar globale config Parameter zu setzen

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

## python virtualenv

python virtualenv erlaubt das anlegen virtueller python environments

```
sudo apt-get install virtualenvwrapper
```

### Vorbereitungen

Folgende Zeilen sollten der Datei ~/.profile angehängt werden:

```
# Virtualenvwrapper
VIRTUALENVWRAPPER_PYTHON=$(which python3)
export WORKON_HOME=~/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
```

Nach einem Neustart des terminals stehen nun die virtualenv Kommandos zur Verfügung

### Environment anlegen

Per default verwenden wir den pyhton3 Interpreter

```
mkvirtualenv __ENVNAME__
```

Das Anlegen einer Environment mit einer anderen Python Version funktioniert wie folgt:

```
mkvirtualenv --python=/usr/bin/python2.7 __ENVNAME__
```

### Environment betreten

```
workon __ENVNAME__
```

### Environment verlassen

```
deactivate
```

### Environment löschen

```
rmvirtualenv __ENVNAME__
```

### Installieren von Paketen

```
pip install __PAKETNAME__
```

### Environment upgrade

Nachdem die entsprechende Environment betreten wurde, können alle installierten Pakete mit folgendem Kommando aktualisiert werden

```
pip freeze — local | grep -v ‘^\-e’ | cut -d = -f 1 | xargs -n1 pip install -U
```

### Environments listen

```
lsvirtualenv
```

## network und analyse tools

```
sudo apt-get install htop nmap tcptraceroute ethstatus
```

## atom

atom ist ein auf Elektron basierender code editor

Zur Installation ist das .deb File von https://atom.io/ herunter zu laden und zu installieren

## VirtualBox

VirtualBox erlaubt das einrichten und starten virtueller Computer auf unserem Host System

Für die Installation von VirtualBox folgen wir den Schritten auf der Website https://www.virtualbox.org/wiki/Linux_Downloads

```
sudo echo 'deb https://download.virtualbox.org/virtualbox/debian bionic contrib' >> /etc/apt/sources.list.d/virtualbox.list
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-5.2
```

Anschließend sollte noch das VirtualBox Extension Pack (https://www.virtualbox.org/wiki/Downloads) herunter geladen und installiert werden

## SSH Key

Nun erstellen wir noch einen SSH Key, welcher zu einem späteren Zeitpunkt benötigt wird

```
ssh-keygen
```
