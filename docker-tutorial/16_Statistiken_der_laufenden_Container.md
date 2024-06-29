In diesem Tutorial lernen wir, wie man Statistiken zum Ressourcenverbrauch und zur Performance der laufenden Docker-Container abruft. Hierbei nutzen wir das Kommando `docker stats`. Dieses Kommando gibt Echtzeitinformationen über die CPU-, Speicher-, Netzwerk- und I/O-Auslastung der Container aus.

### Docker Stats Befehl

Der Befehl `docker stats` wird verwendet, um Statistiken für alle laufenden Container anzuzeigen. Der allgemeine Aufbau des Befehls lautet:

```sh
docker stats [OPTIONS] [CONTAINER...]
```

### Beispiel

Um die Statistiken aller laufenden Container anzuzeigen, geben wir einfach folgendes Kommando in die Terminal ein:

```sh
docker stats
```

Um die Statistiken für einen spezifischen Container anzuzeigen, fügen wir die Container-ID oder den Namen hinzu:

```sh
docker stats <container_id_or_name>
```

### Erklärungen der Ausgabe

Beim Ausführen des `docker stats` Befehls erhalten wir eine Tabelle mit folgenden Spalten:

- **CONTAINER ID**: Die eindeutige ID des Containers.
- **NAME**: Der Name des Containers.
- **CPU %**: Der CPU-Nutzungsprozentsatz des Containers.
- **MEM USAGE / LIMIT**: Der aktuelle und maximale Speicherverbrauch des Containers.
- **MEM %**: Der Speicherverbrauchsprozentsatz des Containers im Verhältnis zum zugewiesenen Speicherlimit.
- **NET I/O**: Netzwerk Input/Output, zeigt den Netzwerkverkehr des Containers.
- **BLOCK I/O**: Block Input/Output, zeigt die I/O-Operationen des Containers auf Blockgeräte (wie Festplatten).
- **PIDS**: Die Anzahl der Prozess-IDs, die der Container verwendet.

### Optionen

Es gibt verschiedene Optionen, die man mit `docker stats` verwenden kann:

- `--all` oder `-a`: Zeigt alle Container an, nicht nur die laufenden.
- `--format` : Gibt die Statistiken in einem bestimmten Format aus.
- `--no-stream` : Gibt nur einen aktuellen Snapshot der Statistiken aus und beendet sich dann.
- `--no-trunc`: Zeigt die vollständigen Container-IDs an, ohne sie abzuschneiden.

### Beispiel mit Optionen

Um beispielsweise die Statistiken nur einmalig anzuzeigen und dann den Befehl zu beenden, nutzen wir:

```sh
docker stats --no-stream
```

Um die Statistiken in einem benutzerdefinierten Format anzuzeigen, verwenden wir:

```sh
docker stats --format "table {{.Container}}\t{{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}"
```

Hier wird die Ausgabe in einem Tabellenformat dargestellt, das nur die Container-ID, den Namen, die CPU-Nutzung und den Speicherverbrauch anzeigt.

### Fazit

Der `docker stats` Befehl ist ein mächtiges Werkzeug, um den Ressourcenverbrauch und die Performance der laufenden Docker-Container in Echtzeit zu überwachen. Durch die verschiedenen Optionen kann die Ausgabe an die eigenen Bedürfnisse angepasst werden, was die Verwaltung und Optimierung der Container erleichtert.

Falls du noch Fragen oder spezielle Anwendungsfälle hast, kannst du gerne nachfragen!