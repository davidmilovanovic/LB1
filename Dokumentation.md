# Modul 300 - Leistungsbeurteilung 1

## Inhaltsverzeichnis
1. [Aufgabenstellung](#Aufgabenstellung)
2. [Voraussetzungen](#Voraussetzungen)
3. [Mein Service](#Mein_Service)

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

## [Mein Service](#){name=Mein-Service}

Bei meinem Service wird ein Webserver erstellt. Auf dem Webserver läuft die Webanwendung phpMyadmin, welches mit dem sql-Server verbunden ist.

![Image](m300Verbindung.png)

#### Zugriff auf den Service

#### Das Vagrantfile

## Sicherheitsaspekte

Um die Sicherheit unseres Services zu schützen, werden in unser Vagrantfile diese drei Sachen hinzugefügt:<br />
* Benutzer mit Rechtevergabe
* Firewall
* Reverse Proxy<br />
Durch die entsprechenden Rechtevergabe können unbefugte Benutzer nicht Dinge machen, die eigentlich nicht für sie Gedacht wären. Mit der Firewall können wir entsprechende Ports öffnen und schliessen. Nur Ports, welche für den Service benötigt sind, sollten offen sein. Durch den Reverse-Proxy ist der Webserver vor direkten Angriffen von aussen gesichert. Die Internetuser kommunizieren mit dem Proxy, und nicht mit dem Webserver.

## Wissenszuwachs



## Reflexion

## Glossar

Vagrant: Mit Vagrant kann man virtuelle Maschinen erstellen und verwalten.

Markdown: Ist eine vereinfachte Auszeichnungssprache.

Apache2: Ist ein Webserver.

phpMyAdmin: Freie Webanwendung zur Administration von MySQL-Datenbanken/MariaDB

SQL-Server: Datenbank mit der Sprache sql
