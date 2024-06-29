### Docker Tutorial #11 - Der Detached Modus

In diesem Tutorial werden wir den Detached Modus in Docker erklären. Der Detached Modus erlaubt es, Container im Hintergrund zu starten, was besonders nützlich ist, wenn man möchte, dass Container im Hintergrund laufen, während man weiter in der Shell arbeiten kann.

#### Was ist der Detached Modus?

Der Detached Modus ist ein Feature von Docker, das es ermöglicht, Container im Hintergrund zu starten und laufen zu lassen. Im Gegensatz zum Standard-Modus, bei dem das Terminal mit dem laufenden Container verbunden bleibt, wird das Terminal im Detached Modus sofort wieder freigegeben.

#### Container im Detached Modus starten

Um einen Container im Detached Modus zu starten, verwendet man das Flag `-d`. Hier ist ein Beispiel:

```bash
docker run -d --name mein_container nginx
```

In diesem Beispiel wird ein Nginx-Container im Hintergrund gestartet und der Container wird `mein_container` genannt.

#### Überprüfen des Container-Status

Um den Status der laufenden Container zu überprüfen, kann man den folgenden Befehl verwenden:

```bash
docker ps
```

Dieser Befehl listet alle laufenden Container auf, zusammen mit Informationen wie Container-ID, Image, Status und Ports.

#### Abrufen der Logs eines Containers

Auch wenn ein Container im Hintergrund läuft, kann man dessen Logs weiterhin einsehen. Hierfür verwendet man den Befehl `docker logs`:

```bash
docker logs mein_container

docker logs <container_id>
```

Dieser Befehl zeigt die Logs des Containers `mein_container` an. Man kann auch das Flag `-f` (follow) hinzufügen, um die Logs in Echtzeit zu verfolgen:

```bash
docker logs -f mein_container

docker logs -f <container_id>
```

#### Zusammenfassung

Der Detached Modus in Docker ist eine einfache und effektive Möglichkeit, Container im Hintergrund zu starten und laufen zu lassen. Hier sind die wichtigsten Befehle, die in diesem Tutorial behandelt wurden:

1. **Container im Detached Modus starten:**
   ```bash
   docker run -d --name mein_container nginx
   ```
2. **Überprüfen des Container-Status:**
   ```bash
   docker ps
   ```
3. **Abrufen der Logs eines Containers:**
   ```bash
   docker logs mein_container
   ```

Mit diesen Befehlen kann man Container im Hintergrund verwalten und deren Status und Logs überprüfen, ohne dass das Terminal blockiert wird.