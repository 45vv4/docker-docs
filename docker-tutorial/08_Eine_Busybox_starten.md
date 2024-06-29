# Docker Tutorial #8 - Eine Busybox starten

In diesem Kapitel lernen wir, wie man einen Busybox-Container startet und einfache Befehle darin ausführt. Busybox ist ein leichtgewichtiges Image, das sich hervorragend für Tests und Debugging eignet. Folgen Sie den unten stehenden Schritten, um einen Busybox-Container zu starten und einige grundlegende Befehle auszuführen.

## Voraussetzungen

- Docker muss auf Ihrem System installiert und konfiguriert sein.

## Schritt 1: Herunterladen des Busybox-Images

Zunächst müssen wir das Busybox-Image von Docker Hub herunterladen. Öffnen Sie ein Terminal und führen Sie den folgenden Befehl aus:

```sh
docker pull busybox
```

## Schritt 2: Starten eines Busybox-Containers

Nachdem das Image heruntergeladen wurde, können wir einen Container daraus starten. Verwenden Sie den folgenden Befehl, um einen Busybox-Container zu starten und in dessen Shell zu wechseln:

```sh
# morpheus tutorial
docker run busybox

docker run -it busybox
```

Die Optionen `-it` stehen für "interaktiv" und "Terminal". Diese Optionen ermöglichen es uns, mit dem Container über die Kommandozeile zu interagieren.

### Docker-Images
Der Befehl docker images listet alle auf Ihrem lokalen Docker-Host gespeicherten Docker-Images mit deren Details wie Repository, Tag, Image ID, Erstellungsdatum und Größe auf.
```sh
docker images
```

#### Docker-Images löschen 
```sh
docker rmi <image-id>
```

### Docker-Container
Der Befehl docker ps listet alle aktuell laufenden Docker-Container auf Ihrem System auf, einschließlich deren Container-ID, Image, Namen, Status und Portinformationen.
```sh
docker ps

```
Alle anzeigen: 
```sh
docker ps -a
```

### Docker-Container löschen
Der Befehl `docker rm <container_id>` entfernt einen oder mehrere gestoppte Docker-Container von Ihrem System.
```sh
docker rm <container_id>
```
#### Alle Docker-Container stoppen
```sh
docker rm $(docker ps -a -q -f status=exited)
```
```sh
sudo docker rm $(sudo docker ps -a -q -f status=exited)
```

Der Befehl `docker container prune` entfernt alle gestoppten Docker-Container von Ihrem System, um Speicherplatz freizugeben. Hier ist ein Beispiel, wie Sie den Befehl verwenden:

```sh
docker container prune
```

Nach dem Ausführen dieses Befehls werden Sie aufgefordert, die Aktion zu bestätigen. Geben Sie `y` ein, um die gestoppten Container zu löschen.

## Schritt 3: Ausführen einfacher Befehle im Container

Nun befinden Sie sich in der Shell des Busybox-Containers und können verschiedene Befehle ausführen. Hier sind einige Beispiele:

### Anzeigen des aktuellen Verzeichnisses

```sh
pwd
```

Dieser Befehl zeigt das aktuelle Arbeitsverzeichnis an, in dem Sie sich befinden. Standardmäßig ist es das Root-Verzeichnis (`/`).

### Auflisten der Dateien im aktuellen Verzeichnis

```sh
ls
```

Dieser Befehl listet die Dateien und Verzeichnisse im aktuellen Verzeichnis auf.

### Erstellen eines neuen Verzeichnisses

```sh
mkdir meinverzeichnis
```

Dieser Befehl erstellt ein neues Verzeichnis mit dem Namen `meinverzeichnis`.

### Wechseln in das neue Verzeichnis

```sh
cd meinverzeichnis
```

Mit diesem Befehl wechseln Sie in das neu erstellte Verzeichnis.

### Erstellen einer neuen Datei

```sh
echo "Hallo, Docker!" > hallo.txt
```

Dieser Befehl erstellt eine neue Datei namens `hallo.txt` und schreibt den Text "Hallo, Docker!" hinein.

### Anzeigen des Inhalts der Datei

```sh
cat hallo.txt
```

Mit diesem Befehl können Sie den Inhalt der Datei `hallo.txt` anzeigen.

## Schritt 4: Verlassen des Containers

Um die Shell des Busybox-Containers zu verlassen und den Container zu stoppen, geben Sie den folgenden Befehl ein:

```sh
exit
```

Der Container wird gestoppt und Sie kehren zu Ihrer lokalen Kommandozeile zurück.

## Zusammenfassung

In diesem Kapitel haben Sie gelernt, wie man einen Busybox-Container startet und einige grundlegende Befehle darin ausführt. Busybox ist ein nützliches Werkzeug für Tests und Debugging und kann Ihnen helfen, Docker besser zu verstehen und zu nutzen.