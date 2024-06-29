### Docker Tutorial #14: Container stoppen, Löschen von Images und Containern

In diesem Tutorial werden wir die notwendigen Schritte und Befehle durchgehen, um Docker-Container zu stoppen und sowohl Docker-Container als auch Docker-Images zu löschen.

#### 1. Container stoppen

Um einen laufenden Container zu stoppen, verwenden wir den Befehl `docker stop` gefolgt von der Container-ID oder dem Namen des Containers.

```bash
docker stop <container_id>
```

Beispiel:
```bash
docker stop my_container
```

Dieser Befehl sendet ein SIGTERM-Signal an den Hauptprozess des Containers, um diesen sanft zu stoppen. Wenn der Container nach einer bestimmten Zeit nicht gestoppt wurde, wird ein SIGKILL-Signal gesendet, um den Container zwangsweise zu beenden.

#### 2. Container löschen

Um einen Container zu löschen, verwenden wir den Befehl `docker rm`. Bevor ein Container gelöscht werden kann, muss er gestoppt sein.

```bash
docker rm <container_id>
```

Beispiel:
```bash
docker rm my_container
```

Falls der Container noch läuft und Sie ihn dennoch löschen möchten, können Sie die Option `-f` (force) verwenden:

```bash
docker rm -f <container_id>
```

Beispiel:
```bash
docker rm -f my_container
```

#### 3. Mehrere Container gleichzeitig löschen

Manchmal möchten Sie möglicherweise mehrere Container gleichzeitig löschen. Dies kann durch Angabe mehrerer Container-IDs oder Namen im selben Befehl erfolgen:

```bash
docker rm <container_id_1> <container_id_2> <container_id_3>
```

Beispiel:
```bash
docker rm container1 container2 container3
```

#### 4. Alle Container löschen

Um alle Container zu löschen, können Sie einen Befehl verwenden, der alle Container-IDs abruft und sie an `docker rm` übergibt:

```bash
docker rm $(docker ps -a -q)
```

#### 5. Docker-Images löschen

Um ein Docker-Image zu löschen, verwenden wir den Befehl `docker rmi` gefolgt von der Image-ID oder dem Tag des Images:

```bash
docker rmi <image_id>
```

Beispiel:
```bash
docker rmi my_image:latest
```

#### 6. Mehrere Images gleichzeitig löschen

Sie können mehrere Images gleichzeitig löschen, indem Sie mehrere Image-IDs oder Tags angeben:

```bash
docker rmi <image_id_1> <image_id_2> <image_id_3>
```

Beispiel:
```bash
docker rmi image1 image2 image3
```

#### 7. Ungenutzte Images löschen

Um alle ungenutzten Docker-Images zu löschen, die nicht mehr von einem Container verwendet werden, können Sie den folgenden Befehl verwenden:

```bash
docker image prune
```

Falls Sie alle ungenutzten Images, Netzwerke und Volumes löschen möchten, können Sie den Befehl erweitern:

```bash
docker system prune
```

#### Zusammenfassung der Befehle

- **Container stoppen:** `docker stop <container_id>`
- **Container löschen:** `docker rm <container_id>`
- **Laufende Container erzwingen und löschen:** `docker rm -f <container_id>`
- **Alle Container löschen:** `docker rm $(docker ps -a -q)`
- **Image löschen:** `docker rmi <image_id>`
- **Mehrere Images löschen:** `docker rmi <image_id_1> <image_id_2>`
- **Ungenutzte Images löschen:** `docker image prune`
- **System bereinigen:** `docker system prune`

Diese Befehle sollten Ihnen helfen, Docker-Container und -Images effizient zu verwalten und Ihre Docker-Umgebung sauber zu halten.