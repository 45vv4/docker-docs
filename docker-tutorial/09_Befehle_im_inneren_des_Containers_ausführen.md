## Docker Tutorial: Befehle im Inneren des Containers Ausführen (Linux, Windows und macOS)

In diesem Tutorial wird erläutert, wie Sie Befehle innerhalb eines laufenden Containers ausführen und den Unterschied zwischen `docker exec` und `docker attach` verstehen. Es gibt separate Abschnitte für Linux-, Windows- und macOS-Benutzer.

### Voraussetzungen
- Docker ist installiert und läuft auf Ihrem System.
- Ein laufender Docker-Container, mit dem Sie arbeiten möchten.

## `docker exec` vs. `docker attach`

- **`docker exec`:**
  - Startet einen neuen Prozess im Container.
  - Kann mehrfach verwendet werden, um verschiedene Prozesse gleichzeitig auszuführen.
  - Führt Befehle aus, ohne die Verbindung zu bestehenden Prozessen zu stören.

- **`docker attach`:**
  - Verbindet sich mit einem bestehenden Prozess.
  - Alle Eingaben werden direkt an den Hauptprozess des Containers gesendet.
  - Ideal zum Verbinden mit einem Hauptprozess wie einer laufenden Server-Anwendung.

### Befehle im Inneren eines Containers ausführen

#### Linux

1. **Starten eines Containers:**
   ```sh
   docker run -it busybox sh
   ```
   Dieser Befehl startet einen interaktiven `busybox` Container und öffnet eine Shell (`sh`) innerhalb des Containers.

2. **Führen Sie verschiedene Befehle im Container aus:**
   - Anzeigen des aktuellen Verzeichnisses:
     ```sh
     pwd
     ```
   - Auflisten des Inhalts des aktuellen Verzeichnisses:
     ```sh
     ls
     ```
   - Erstellen eines neuen Verzeichnisses:
     ```sh
     mkdir /mydir
     ```
   - Navigieren zu dem neuen Verzeichnis:
     ```sh
     cd /mydir
     ```
   - Erstellen einer neuen Datei:
     ```sh
     echo "Hello, World!" > hello.txt
     ```
   - Anzeigen des Inhalts der Datei:
     ```sh
     cat hello.txt
     ```

3. **Verlassen des Containers:**
   ```sh
   exit
   ```

#### Windows

Wenn Sie Docker unter Windows in einer Umgebung wie Git Bash oder MinTTY ausführen, müssen Sie den Befehl mit `winpty` ausführen, um den Fehler "the input device is not a TTY" zu vermeiden.

1. **Starten eines Containers:**
   ```sh
   winpty docker run -it busybox sh
   ```

2. **Führen Sie verschiedene Befehle im Container aus:**
   - Anzeigen des aktuellen Verzeichnisses:
     ```sh
     pwd
     ```
   - Auflisten des Inhalts des aktuellen Verzeichnisses:
     ```sh
     ls
     ```
   - Erstellen eines neuen Verzeichnisses:
     ```sh
     mkdir /mydir
     ```
   - Navigieren zu dem neuen Verzeichnis:
     ```sh
     cd /mydir
     ```
   - Erstellen einer neuen Datei:
     ```sh
     echo "Hello, World!" > hello.txt
     ```
   - Anzeigen des Inhalts der Datei:
     ```sh
     cat hello.txt
     ```

3. **Verlassen des Containers:**
   ```sh
   exit
   ```

#### macOS

Für macOS-Benutzer sind die Schritte ähnlich wie bei Linux.

1. **Starten eines Containers:**
   ```sh
   docker run -it busybox sh
   ```
   Dieser Befehl startet einen interaktiven `busybox` Container und öffnet eine Shell (`sh`) innerhalb des Containers.

2. **Führen Sie verschiedene Befehle im Container aus:**
   - Anzeigen des aktuellen Verzeichnisses:
     ```sh
     pwd
     ```
   - Auflisten des Inhalts des aktuellen Verzeichnisses:
     ```sh
     ls
     ```
   - Erstellen eines neuen Verzeichnisses:
     ```sh
     mkdir /mydir
     ```
   - Navigieren zu dem neuen Verzeichnis:
     ```sh
     cd /mydir
     ```
   - Erstellen einer neuen Datei:
     ```sh
     echo "Hello, World!" > hello.txt
     ```
   - Anzeigen des Inhalts der Datei:
     ```sh
     cat hello.txt
     ```

3. **Verlassen des Containers:**
   ```sh
   exit
   ```

### Verwendung von `docker exec`

#### Linux und macOS

1. **Laufende Container auflisten:**
   ```sh
   docker ps
   ```
   Dies listet alle laufenden Container auf. Finden Sie die Container-ID oder den Namen des Containers, in dem Sie Befehle ausführen möchten.

2. **Einen Befehl im Container ausführen:**
   Verwenden Sie die Container-ID oder den Namen zusammen mit dem gewünschten Befehl. Hier sind einige Beispiele:

   - **Starten einer interaktiven Shell:**
     ```sh
     docker exec -it CONTAINER_ID sh
     ```
     Beispiel:
     ```sh
     docker exec -it 224a6dbb5c37 sh
     ```

   - **Ausführen eines einfachen Befehls:**
     ```sh
     docker exec -it CONTAINER_ID COMMAND
     ```
     Beispiel:
     ```sh
     docker exec -it 224a6dbb5c37 ls /var
     ```

#### Windows

1. **Laufende Container auflisten:**
   ```sh
   docker ps
   ```
   Dies listet alle laufenden Container auf. Finden Sie die Container-ID oder den Namen des Containers, in dem Sie Befehle ausführen möchten.

2. **Einen Befehl im Container ausführen:**
   Verwenden Sie die Container-ID oder den Namen zusammen mit dem gewünschten Befehl. Hier sind einige Beispiele:

   - **Starten einer interaktiven Shell:**
     ```sh
     winpty docker exec -it CONTAINER_ID sh
     ```
     Beispiel:
     ```sh
     winpty docker exec -it 224a6dbb5c37 sh
     ```

   - **Ausführen eines einfachen Befehls:**
     ```sh
     winpty docker exec -it CONTAINER_ID COMMAND
     ```
     Beispiel:
     ```sh
     winpty docker exec -it 224a6dbb5c37 ls /var
     ```

### Zusammenfassung

Mit `docker exec` können Sie neue Prozesse in einem laufenden Container starten, während `docker attach` Sie mit dem bestehenden Hauptprozess des Containers verbindet. Unter Windows kann `winpty` verwendet werden, um TTY-Probleme zu vermeiden. Befolgen Sie diese Anweisungen, um effizient mit Containern auf Linux-, Windows- und macOS-Systemen zu arbeiten.