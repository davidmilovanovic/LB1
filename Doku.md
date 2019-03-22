# Modul 300 - Leistungsbeurteilung 1

## Inhaltsverzeichnis
1. [Aufgabenstellung](#Aufgabenstellung)
2. [Voraussetzungen](#Voraussetzungen)
3. [Mein Service](#id-section2)
4. [Sicherheitsaspekte](#Voraussetzungen)
5. [Wissenszuwachs](#Voraussetzungen)

## Aufgabenstellung

Die LB1 besteht darin, ein Service zur Verfügung zu stellen. Dieser Service sollte mit dem starten eines Vagrantfiles ohne weitere Konfigurationen starten. Das ganze sollte anschliessend mit Markdown dokumentiert werden. Die Bewertungskriterien findet man [hier](https://bscw.tbz.ch/bscw/bscw.cgi/d29084554/M300_LB1_Bewertungsraster.pdf?op=get&open=1).

## Voraussetzungen
Damit der Service erstellt werden kann, müssen vorerst einige Dinge noch erledigt werden:

**GitHub Account**<br />
GitHub dient sozusagen als Cloud-Speicher unserer Dateien und Dokumentationen.

**ssh Keys**<br />
Die ssh schlüssel ermöglichen uns, eine verschlüsselte Netzwerkverbindung aufzubauen.

**Git Client**<br />
Um unsere Dateien von GitHub auf unseren lokalen Comupter zu holen, benötigen wir Git client. Unter Windows nennt sich das Git/Bash.

**VirtualBox**<br />
Zueinem benötigen wir einen Hypervisor, welcher unsere VMs erstellt. In unserem Fall benutzen wir VirtualBox, da bei Vagrant Boxes dieser Hypervisor überall unterstützt wird.

**Vagrant**<br />
Damit unser Client überhaupt Vagrant versteht, muss Vagrant von ihrer Webseite heruntergeladen werden.

**Visual Studio Code**<br />
Alle lokalen Repositories an einem Ort zu verwalten und die dazugehörigen Dateien zu bearbeiten ermöglicht uns Visual Studio Code. Stduio Code kann man sich ganz einfach von ihrer Webseite herunterladen.

Die genaue Anleitung für die installationen:
[Kapitel 20](https://github.com/mc-b/M300/blob/master/10-Toolumgebung/README.md)

## Netzwerkplan

![Image](test.png)        

<div id='id-section2'/>

## Mein Service

Bei meinem Service wird ein Webserver erstellt. Auf dem Webserver läuft die Webanwendung phpMyadmin, welches mit dem sql-Server verbunden ist.


#### Zugriff auf den Service

#### Das Vagrantfile

## Sicherheitsaspekte

Um die Sicherheit unseres Services zu schützen, werden in unser Vagrantfile diese drei Sachen hinzugefügt:<br />
* Benutzer mit Rechtevergabe
* Firewall
* Reverse Proxy<br />
Durch die entsprechenden Rechtevergabe können unbefugte Benutzer nicht Dinge machen, die eigentlich nicht für sie Gedacht wären. Mit der Firewall können wir entsprechende Ports öffnen und schliessen. Nur Ports, welche für den Service benötigt sind, sollten offen sein. Durch den Reverse-Proxy ist der Webserver vor direkten Angriffen von aussen gesichert. Die Internetuser kommunizieren mit dem Proxy, und nicht mit dem Webserver.

## Testing

| Testfall                                                                                               | Resultat                                                                                                                                |
|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Vom Client auf http://localhost:80 zugreifen.                                                                 | Funktioniert. Die Default Page des Webservers wird angezeigt.                                                        |
| Vom Client (192.168.40.1) auf http://localhost:80/phpmyadmin                                           | Funktioniert. Phpmyadmin Startseite wird angezeigt.                                     |
| git clone                                                                                              | Funktioniert einwandfrei                                                        |

  

## Wissenszuwachs
Im Geschäft habe ich Mal mit git gearbeitet. Alles andere musste ich neu dazulernen. Ich weiss jetzt wie Vagrant funktioniert, wie man es Konfigurieren muss und nötigen Befehle dazu.


| Command           | Beschreibung                                                                                                                                                                                                                                                                              |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| vagrant up        | Startet virtuelle Maschine                                                                                                                                                                                                                                                                    |
| vagrant halt      | Stoppt virtuelle Maschine                                                                                                                                                                                                                                                                     |
| vagrant destroy   | Zerstört die virtuelle Maschine. Der Source Code und der Inhalt des Data-Verzeichnisses bleiben unverändert. Nur die VirtualBox Maschinen-Instanz wird zerstört. |
| vagrant provision | Neukonfiguration der virtuellen Maschine nach einer Source Code Änderung.                                                                                                                                                                                                                               |
| vagrant reload    | Neuladen der virtuellen Maschine. Nützlich, wenn man die Einstellungen zu dem Netzwerk oder einen synchronisierten Ordner ändern will.                                                                                                                                                                                             |



## Reflexion
Bis jetzt konnte ich vieles neues lernen. Leider habe ich es nicht geschafft, mein Service auf zwei Server aufzuteilen. Insgesamt war es aber keine leichte arbeit. Am schwierigsten war es, die Prompt Befehle, welche bei einer Installation auftreten, zu bestätigen. Das ganze Projekt habe ich alleine ohne hilfe gemacht. Schlussendlich wurden viele Stunden dafür geopfert, jedoch wurde vieles dazugelernt.

## Glossar

Vagrant: Mit Vagrant kann man virtuelle Maschinen erstellen und verwalten.

Markdown: Ist eine vereinfachte Auszeichnungssprache.

Apache2: Ist ein Webserver.

phpMyAdmin: Freie Webanwendung zur Administration von MySQL-Datenbanken/MariaDB

SQL-Server: Datenbank mit der Sprache sql
