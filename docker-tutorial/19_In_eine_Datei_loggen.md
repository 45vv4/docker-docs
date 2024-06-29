[Docker Tutorial #19 - In eine Datei loggen](https://www.youtube.com/watch?v=JwKPbh-6K_Q&list=PLNmsVeXQZj7oea6IDCLzpKe5XfLmWCwgr&index=21)

Um Docker-Logs in Dateien zu speichern, müssen wir den Docker-Daemon so konfigurieren, dass er das File-Logging verwendet. Hier sind die Schritte, um dies zu erreichen:

### Schritt 1: Docker Daemon konfigurieren

1. **Öffnen Sie die Docker Daemon Konfigurationsdatei:**
   - Unter Linux befindet sich die Docker Daemon Konfigurationsdatei normalerweise unter `/etc/docker/daemon.json`.
   - Wenn die Datei nicht existiert, erstellen Sie sie.

2. **Konfigurieren Sie das File-Logging:**
   - Fügen Sie die Konfiguration für das File-Logging hinzu oder ändern Sie sie. Ein Beispiel für eine `daemon.json`-Datei, die File-Logging konfiguriert, sieht wie folgt aus:

     ```json
     {
       "log-driver": "json-file",
       "log-opts": {
         "max-size": "10m",
         "max-file": "3"
       }
     }
     ```

   - Diese Konfiguration stellt sicher, dass Docker Logs im JSON-Format in Dateien speichert, jede Log-Datei maximal 10 MB groß sein darf und maximal 3 Dateien behalten werden.

### Schritt 2: Docker Daemon neu starten

Nach dem Ändern der Konfigurationsdatei müssen Sie den Docker-Daemon neu starten, damit die Änderungen wirksam werden:

- Unter Linux verwenden Sie den folgenden Befehl:

  ```sh
  sudo systemctl restart docker
  ```

### Schritt 3: Überprüfen der Log-Konfiguration

1. **Starten Sie einen Docker-Container:**
   - Führen Sie einen Container aus, um sicherzustellen, dass die Logging-Konfiguration funktioniert. Zum Beispiel:

     ```sh
     docker run -d --name test-container busybox sh -c "while true; do echo hello world; sleep 1; done"
     ```

2. **Überprüfen Sie die Log-Dateien:**
   - Die Logs für den Container sollten jetzt im Verzeichnis `/var/lib/docker/containers/<container-id>/` gespeichert sein. Sie können die Logs anzeigen, indem Sie die entsprechende Log-Datei lesen. Zum Beispiel:

     ```sh
     sudo cat /var/lib/docker/containers/<container-id>/<container-id>-json.log
     ```

### Optional: Logs in ein spezifisches Verzeichnis umleiten

Wenn Sie die Logs in ein spezifisches Verzeichnis umleiten möchten, können Sie symbolische Links verwenden oder das Verzeichnis `/var/lib/docker/containers/` ändern. Das Ändern des Standardverzeichnisses für Docker-Daten kann jedoch komplex sein und erfordert möglicherweise zusätzliche Konfiguration.

Mit diesen Schritten sollten Sie in der Lage sein, Docker-Logs in Dateien zu speichern und die notwendigen Einstellungen vorzunehmen, um das File-Logging zu konfigurieren.