### Docker Tutorial #12 - Eine Shell im Detached Mode erlangen

In diesem Tutorial lernst du, wie du eine interaktive Shell in einem im Detached Mode laufenden Docker-Container erhältst. Es gibt zwei Hauptmethoden: `docker exec` und `docker attach`.

#### Methode 1: `docker exec`

1. **Container im Detached Mode starten**:
   ```bash
   docker run -d --name mein_container ubuntu
   ```
   Dieser Befehl startet einen Container im Hintergrund (Detached Mode) mit dem Namen `mein_container` basierend auf dem Ubuntu-Image.

2. **Eine interaktive Shell im Container starten**:
   ```bash
   docker exec -it mein_container bash
   ```
   Mit diesem Befehl öffnest du eine interaktive Bash-Shell im laufenden Container.

#### Methode 2: `docker attach`

1. **Container im Detached Mode starten**:
   ```bash
   docker run -d --name mein_container ubuntu
   ```

2. **Zu dem Container verbinden**:
   ```bash
   docker attach mein_container
   ```
   Mit diesem Befehl verbindest du dich direkt mit dem Standard-Eingabekanal des Containers. Beachte, dass `docker attach` die gleiche Ausgabe zeigt, die der Container ursprünglich anzeigt. Es ist nicht so flexibel wie `docker exec`, aber nützlich, wenn du mit dem Hauptprozess des Containers interagieren möchtest.

#### Vergleich der Methoden

- **`docker exec`**:
  - Startet eine neue Shell im laufenden Container.
  - Ermöglicht mehrere gleichzeitige Verbindungen.
  - Ideal für administrative Aufgaben oder Debugging.
  
- **`docker attach`**:
  - Verbindet sich mit der Hauptshell des Containers.
  - Es kann zu Problemen kommen, wenn mehrere Nutzer versuchen, sich gleichzeitig zu verbinden.
  - Nützlich, wenn du mit dem Hauptprozess des Containers arbeiten möchtest.

### Beispielanwendung

Angenommen, du hast einen Nginx-Container im Detached Mode laufen und möchtest die Konfigurationsdateien überprüfen oder ändern.

1. **Nginx-Container im Detached Mode starten**:
   ```bash
   docker run -d --name nginx_container nginx
   ```

2. **Mit `docker exec` eine interaktive Shell starten**:
   ```bash
   docker exec -it nginx_container bash
   ```

3. **Mit `docker attach` zum Container verbinden** (weniger üblich für Nginx, aber möglich):
   ```bash
   docker attach nginx_container
   ```

Mit diesen Schritten solltest du in der Lage sein, auf eine Shell in einem im Detached Mode laufenden Container zuzugreifen und administrative Aufgaben durchzuführen.