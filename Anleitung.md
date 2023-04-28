Skip to content
Search or jump to…
Pull requests
Issues
Codespaces
Marketplace
Explore
 
@neunnulleinsvier 
neunnulleinsvier
/
miniprojekt-m169
Private
Cannot fork because you own this repository and are not a member of any organizations.
Code
Issues
Pull requests
Actions
Projects
Security
Insights
Settings
Beta Try the new code view
miniprojekt-m169/Aleitung.md
@neunnulleinsvier
neunnulleinsvier Update Aleitung.md
Latest commit 6606e28 last month
 History
 1 contributor
44 lines (25 sloc)  1.8 KB
 

# Website über einen Container auf Linux hosten

In diesem Tutorial werden wir erkunden, wie Sie eine Website über einen Container auf Linux hosten können. Durch die Verwendung von Containern können wir isolierte Umgebungen erstellen, die alle notwendigen Komponenten haben, um unsere Website auszuführen, ohne Abhängigkeiten direkt auf unserem Host-Computer zu installieren.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- Ein Linux-VM mit Docker installiert und einer bestehenden Internet-Verbindung
- Eine Website, die gehostet werden kann


## Schritt 1: Erstellen Sie ein Dockerfile

Zuerst müssen wir ein Dockerfile erstellen, das die Konfiguration des Containers definiert:

```txt
FROM httpd:2.4
COPY ./public-html/ /usr/local/apache2/htdocs/
```

Speichern Sie diese Datei als `Dockerfile` in einem Verzeichnis auf Ihrem Host-Computer.

## Schritt 2: Bauen Sie das Docker-Image

Jetzt, da wir unser Dockerfile haben, können wir das Docker-Image erstellen. Öffnen Sie ein Terminal und navigieren Sie zum Verzeichnis, das Ihr `Dockerfile` enthält. Führen Sie dann den folgenden Befehl aus:

```txt
docker build -t my-apache2 .
```

Dies erstellt das Docker-Image mit dem Tag `mywebsite`.

## Schritt 3: Führen Sie den Docker-Container aus

Sobald das Docker-Image erstellt ist, können wir den Container ausführen. Hier ist ein Beispielbefehl, um den Container auszuführen und den Port 8080 auf unseren Host-Computer zu mappen:
```txt
sudo docker run -d -p 8080:80 -v /var/log/mywebsite/var/log/mywebsite my-apache2:latest
```

Dies startet den Container und macht den phpmyadmin-Webserver über Port 8080 auf Ihrem Host-Computer zugänglich. Das `-v` im Befehl sorgt dafür, dass ein separates volume auf der Hostmaschine angelegt wird, in der die Logdateien abgelegt werden. 



Footer
© 2023 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
miniprojekt-m169/Aleitung.md at main · neunnulleinsvier/miniprojekt-m169
