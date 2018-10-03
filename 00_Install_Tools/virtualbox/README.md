# VirtualBox Einführung

VirtualBox erlaubt das Konfigurieren und Starten von virtuellen Computern/Servern auf dem eigenen Rechner

## OS Image

Um einen virtuellen Server einzurichten wird ein Installations Medium benötigt. Die Demonstration findet auf Basis eines Ubuntu Server LTS Image statt. Dieses wird unter dem folgenden Link herunter geladen:

https://www.ubuntu.com/download/server

## Virtuelle Maschine erstellen

VirtualBox wird geöffnet und anschließend auf "Neu" geklickt

![Virtuelle Maschine erstellen](images/neu.png "Virtuelle Maschine erstellen")

Name und Betriebssystem festlegen

![Name und Betriebssystem](images/os.png "Name und Betriebssystem")

Speichergröße festlegen

![Speichergröße](images/ram.png "Speichergröße")

Festplatte erzeugen

![Festplatte erzeugen Schritt 1](images/hdd1.png "Festplatte erzeugen Schritt 1")

![Festplatte erzeugen Schritt 2](images/hdd1.png "Festplatte erzeugen Schritt 2")

![Festplatte erzeugen Schritt 3](images/hdd1.png "Festplatte erzeugen Schritt 3")

![Festplatte erzeugen Schritt 4](images/hdd1.png "Festplatte erzeugen Schritt 4")

## Virtuelle Maschine Konfigurieren

Die gewünschte Maschine wird ausgewält und anschließend auf "Ändern" geklickt

![Maschine ändern](images/change.png "Maschine ändern")

System -> Hauptplatine: Diskette abwählen und Zeigegerät auf PS/2-Maus umstellen

![System Hauptplatine](images/system-main.png "System Hauptplatine")

System -> Prozessor: Dem Prozessor der virtuellen Maschine dürfen mindestens 2 Kerne zugeteilt werden

![System Prozessor](images/system-cpu.png "System Prozessor")

Massenspeicher: Auf das CD Symbol mit Pfeil nach unten neben "Optisches laufwerk" klicken und "Datei für optisches Medium auswählen..." klicken

![OS Image auswählen Schritt 1](images/image1.png "OS Image auswählen Schritt 1")

Massenspeicher: Das zuvor herunter geladene Ubuntu Server Image suchen und auswählen

![OS Image auswählen Schritt 2](images/image2.png "OS Image auswählen Schritt 2")

Massenspeicher: Das Image sollte nun für den Controller: IDE ausgewählt sein

![OS Image auswählen Schritt 3](images/image3.png "OS Image auswählen Schritt 3")

Audio: Audio abwählen, da der Server keine Audio Schnittstelle benötigt

![Audio](images/audio.png "Audio")

Netzwerk: Netzwerktyp "Netzwerkbrücke" wählen

![Netzwerk](images/network.png "Netzwerk")

Nach abschließender Konfiguration kann die Maschine gestartet werden

## Maschine installieren

Nach dem Start der Maschine läuft der Installations Prozess der Ubuntu Server Installationsmediums durch

![OS Install Schritt 1](images/install1.png "OS Install Schritt 1")

![OS Install Schritt 2](images/install2.png "OS Install Schritt 2")

![OS Install Schritt 3](images/install3.png "OS Install Schritt 3")

![OS Install Schritt 4](images/install4.png "OS Install Schritt 4")

![OS Install Schritt 5](images/install5.png "OS Install Schritt 5")

![OS Install Schritt 6](images/install6.png "OS Install Schritt 6")

![OS Install Schritt 7](images/install7.png "OS Install Schritt 7")

![OS Install Schritt 8](images/install8.png "OS Install Schritt 8")

![OS Install Schritt 9](images/install9.png "OS Install Schritt 9")

![OS Install Schritt 10](images/install10.png "OS Install Schritt 10")

![OS Install Schritt 11](images/install11.png "OS Install Schritt 11")

![OS Install Schritt 12](images/install12.png "OS Install Schritt 12")

![OS Install Schritt 13](images/install13.png "OS Install Schritt 13")

![OS Install Schritt 14](images/install14.png "OS Install Schritt 14")

## IP Adresse ermitteln

Nach dem Reboot meldet sich der Login Dialog

![Login](images/login.png "Login")

Nach Verwendung der Login Daten, welche während der Installation vergeben wurden, wird die IP Adresse durch die Eingabe folgenden Kommandos ermittelt:

```
ip a
```

![ip a](images/ipa.png "ip a")

Aus der Ausgabe geht hervor, dass die Beispiel Maschine die IP Adresse "192.168.178.104" besitzt

## Die neue Maschine verwenden

Um die neue Maschine zu benutzen, wird nun unter Verwendung des Snapcraft Paketmanagers das Open Source Kanban Board Wekan installiert

Dazu wird die Maschine als erstes per SSH vom Host aus betreten

```
ssh me@192.168.178.104
```

Anschließend wird auf den "root" User gewechselt

```
sudo -i
```

Nun wird der Snap Paketmanager installiert

```
apt install snapd
```

Mit den folgenden Kommandos wird nun Wekan installiert und konfiguriert

```
snap install wekan
snap set wekan root-url="http://192.168.178.104/wekan"
snap set wekan port='80'
systemctl restart snap.wekan.wekan
```

Nach Abschluss der Installation lässt sich das Wekan Board im Browser öffnen

http://192.168.178.104/wekan
