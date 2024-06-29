### Docker Tutorial #13 - Dateien an Container übergeben

In diesem Kapitel werden wir lernen, wie man Dateien zwischen dem Host und einem Docker-Container kopieren kann. Außerdem wird erklärt, wie man Verzeichnisse zwischen Host und Container einbindet. Dafür nutzen wir den Befehl `docker cp` und das Volume-Flag `-v`.

#### Dateien vom Host in den Container kopieren

Um eine Datei oder ein Verzeichnis vom Host in einen Container zu kopieren, nutzen wir den Befehl `docker cp`. Das allgemeine Format des Befehls ist:

```
docker cp <Quelle> <Container-ID>:<Zielpfad>
```

- **Quelle:** Der Pfad zur Datei oder zum Verzeichnis auf dem Host.
- **Container-ID:** Die ID oder der Name des Zielcontainers.
- **Zielpfad:** Der Pfad im Container, wohin die Datei oder das Verzeichnis kopiert werden soll.

Beispiel: Kopieren einer Datei `example.txt` vom Host in den Container:

```sh
docker cp /pfad/zur/example.txt container_id:/pfad/im/container
```

#### Dateien vom Container zum Host kopieren

Der umgekehrte Vorgang, also das Kopieren von Dateien oder Verzeichnissen aus einem Container auf den Host, wird ebenfalls mit `docker cp` durchgeführt. Das Format ist:

```
docker cp <Container-ID>:<Quelle> <Zielpfad>
```

- **Quelle:** Der Pfad zur Datei oder zum Verzeichnis im Container.
- **Container-ID:** Die ID oder der Name des Containers, aus dem kopiert wird.
- **Zielpfad:** Der Pfad auf dem Host, wohin die Datei oder das Verzeichnis kopiert werden soll.

Beispiel: Kopieren einer Datei `example.txt` vom Container auf den Host:

```sh
docker cp container_id:/pfad/im/container/example.txt /pfad/zum/host
```

#### Beispiel-Workflow für das Kopieren

1. **Vorbereitung**: Erstellen einer Beispieltextdatei auf dem Host:
   
   ```sh
   echo "Hello, Docker!" > example.txt
   ```

2. **Container starten**: Starten eines neuen Containers (z.B. mit einem Ubuntu-Image):

   ```sh
   docker run -d --name mycontainer ubuntu sleep infinity
   ```

3. **Datei in den Container kopieren**:

   ```sh
   docker cp example.txt mycontainer:/example.txt
   ```

4. **Überprüfung**: Verbinden zum Container und Überprüfung, ob die Datei vorhanden ist:

   ```sh
   docker exec -it mycontainer bash
   cat /example.txt
   ```

5. **Datei aus dem Container zum Host kopieren**:

   ```sh
   docker cp mycontainer:/example.txt /pfad/zum/host/example_copy.txt
   ```

#### Verzeichnisse einbinden mit Volumes

Um ein Verzeichnis vom Host in einen Container einzubinden, nutzen wir das Volume-Flag `-v`. Dies ermöglicht es uns, Daten persistent zu speichern und von beiden Umgebungen aus darauf zuzugreifen.

Das allgemeine Format für das Einbinden eines Volumes ist:

```
docker run -v <Host-Verzeichnis>:<Container-Verzeichnis> <Image>
```

Beispiel: Starten eines Nginx-Containers und Einbinden eines Verzeichnisses:

```sh
docker run -p 80:80 -d -v '/download/index.html - Docker/nginx-files':/usr/share/nginx/html nginx
```

- **-p 80:80**: Mappt den Port 80 des Hosts auf den Port 80 des Containers.
- **-d**: Führt den Container im Hintergrund aus.
- **-v '/download/index.html - Docker/nginx-files':/usr/share/nginx/html**: Bindet das Verzeichnis `/download/index.html - Docker/nginx-files` vom Host in das Verzeichnis `/usr/share/nginx/html` im Container ein.
- **nginx**: Das Docker-Image, das genutzt wird.

#### Fazit

Mit den Befehlen `docker cp` und `docker run -v` können wir Dateien und Verzeichnisse effektiv zwischen dem Host und Containern übertragen und einbinden. Dies ist besonders nützlich für die Arbeit mit Konfigurationsdateien, Skripten oder statischen Dateien wie HTML-Seiten.

Weiterführende Informationen finden Sie in der [offiziellen Docker-Dokumentation](https://docs.docker.com/engine/reference/commandline/cp/).