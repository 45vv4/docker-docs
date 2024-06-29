[Docker Tutorial #17 - Die Ressourcen eines Containers limitieren (Unter Linux)](https://www.youtube.com/watch?v=9k12DF-zuO4&list=PLNmsVeXQZj7oea6IDCLzpKe5XfLmWCwgr&index=19)

In diesem Kapitel lernst du, wie du die Ressourcen eines Docker-Containers limitieren kannst. Das beinhaltet sowohl CPU als auch RAM Beschränkungen. Wir werden Docker-Compose und die entsprechenden Docker-Befehle verwenden, um diese Limits zu setzen.

### CPU und RAM Limits mit Docker-Compose setzen

#### Beispiel einer Docker-Compose Datei
Hier ist ein Beispiel einer `docker-compose.yml` Datei, die CPU und RAM Limits für einen Container definiert:

```yaml
version: '3.7'
services:
  my_service:
    image: my_image
    deploy:
      resources:
        limits:
          cpus: '0.5'       # Limitiert den Container auf 50% einer CPU
          memory: 512M      # Limitiert den Container auf 512 MB RAM
        reservations:
          cpus: '0.25'      # Reserviert 25% einer CPU für den Container
          memory: 256M      # Reserviert 256 MB RAM für den Container
```

In diesem Beispiel:
- Die CPU-Nutzung des Containers ist auf 50% einer CPU begrenzt.
- Der Container kann maximal 512 MB RAM verwenden.
- 25% einer CPU und 256 MB RAM sind für den Container reserviert.

#### Ausführen des Containers mit Docker-Compose
Speichere die obige Konfiguration in einer Datei namens `docker-compose.yml` und führe dann den folgenden Befehl aus, um den Container zu starten:

```sh
docker-compose up -d
```

### CPU und RAM Limits mit Docker-Befehlen setzen

#### RAM Limitierung
Du kannst die RAM Nutzung eines Containers direkt beim Starten mit dem `--memory` Flag begrenzen:

```sh
docker run -d --name my_container --memory 512m my_image
```

#### CPU Limitierung
Die CPU Nutzung kann ebenfalls mit dem `--cpus` Flag begrenzt werden:

```sh
docker run -d --name my_container --cpus 0.5 my_image
```

### Ressourcenlimitierungen überprüfen

#### Überprüfen der Limits eines laufenden Containers
Du kannst die gesetzten Limits eines laufenden Containers mit folgendem Befehl überprüfen:

```sh
docker inspect my_container
```

Suche nach dem Abschnitt `HostConfig` in der Ausgabe. Hier findest du die CPU und RAM Limits, die für den Container gesetzt wurden.

### Zusammenfassung

- **Docker-Compose:** Definiere Ressourcenlimits in der `docker-compose.yml` Datei unter `deploy.resources`.
- **Docker-Befehle:** Verwende `--memory` und `--cpus` Flags, um RAM und CPU Limits direkt beim Starten eines Containers zu setzen.
- **Überprüfen:** Nutze `docker inspect`, um die gesetzten Limits eines laufenden Containers zu überprüfen.

Diese Methoden ermöglichen es dir, die Ressourcen eines Containers zu kontrollieren und so sicherzustellen, dass er nicht mehr als die zugewiesenen Ressourcen verbraucht.


### Docker Tutorial #19 - In eine Datei loggen (Docker Compose Edition)

In diesem Tutorial erfahren Sie, wie Sie Docker-Logs in Dateien speichern können, wenn Sie Docker Compose verwenden. Das Speichern von Logs in Dateien ist hilfreich für die spätere Analyse und Archivierung. Wir konfigurieren die Docker-Compose-Datei für das File-Logging und zeigen die notwendigen Einstellungen.

#### 1. Docker Compose Datei-Konfiguration

Docker Compose ermöglicht es Ihnen, Log-Optionen für einzelne Dienste direkt in der `docker-compose.yml`-Datei zu definieren. Wir verwenden den `json-file` Log-Driver und passen die Log-Optionen an.

#### Beispiel `docker-compose.yml`

Hier ist ein Beispiel für eine `docker-compose.yml`-Datei, in der die Log-Optionen für einen Nginx-Dienst konfiguriert sind:

```yaml
version: '3.8'

services:
  web:
    image: nginx
    container_name: nginx_container
    ports:
      - "80:80"
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
```

In diesem Beispiel:

- **`driver: "json-file"`**: Setzt den Log-Driver auf `json-file`.
- **`max-size: "10m"`**: Begrenzt die maximale Größe einer Log-Datei auf 10 Megabyte.
- **`max-file: "3"`**: Begrenzt die Anzahl der Log-Dateien auf 3.

#### 2. Docker Compose Stack starten

Nachdem Sie Ihre `docker-compose.yml`-Datei konfiguriert haben, können Sie den Stack mit den folgenden Befehlen starten:

```bash
docker-compose up -d
```

Dieser Befehl startet alle definierten Dienste im Hintergrund.

#### 3. Logs anzeigen

Sie können die Logs der einzelnen Dienste mit dem folgenden Befehl anzeigen:

```bash
docker-compose logs <service-name>
```

Beispiel:

```bash
docker-compose logs web
```

#### 4. Log-Optionen für mehrere Dienste

Wenn Sie mehrere Dienste haben, können Sie die Log-Optionen für jeden Dienst individuell konfigurieren. Hier ist ein erweitertes Beispiel:

```yaml
version: '3.8'

services:
  web:
    image: nginx
    container_name: nginx_container
    ports:
      - "80:80"
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"

  database:
    image: postgres
    container_name: postgres_container
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    logging:
      driver: "json-file"
      options:
        max-size: "5m"
        max-file: "5"
```

In diesem Beispiel haben wir zwei Dienste (`web` und `database`), und jeder Dienst hat seine eigenen Log-Optionen.

#### 5. Logs in benutzerdefinierte Dateien umleiten

Falls Sie Logs in eine spezifische Datei außerhalb des Standard-Docker-Verzeichnisses umleiten möchten, können Sie symbolische Links verwenden. Dies wird allerdings auf Containerebene und nicht direkt über Docker Compose konfiguriert.

#### Fazit

Durch die Konfiguration der `docker-compose.yml`-Datei für das File-Logging können Sie Logs effizient verwalten und speichern. Diese Logs sind nützlich für die Analyse und Fehlerbehebung Ihrer Anwendungen. Nutzen Sie die oben genannten Schritte, um Ihre Docker-Logs in Dateien zu speichern und nach Bedarf anzupassen.