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