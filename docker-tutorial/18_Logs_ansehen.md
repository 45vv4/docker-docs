### Docker Tutorial #18 - Logs ansehen

In diesem Tutorial erfahren Sie, wie Sie Logs von Docker-Containern abrufen und analysieren können. Logs sind ein wesentlicher Bestandteil beim Debuggen und Überwachen von Anwendungen. Docker bietet mehrere Möglichkeiten, um Logs aus Containern zu extrahieren und zu verwalten. Wir werden uns die Verwendung des `docker logs`-Befehls und die Konfiguration von Log-Driver ansehen.

#### 1. Verwendung von `docker logs`

Der `docker logs`-Befehl wird verwendet, um die Logs eines laufenden oder gestoppten Containers anzuzeigen. Hier sind die grundlegenden Schritte zur Verwendung dieses Befehls:

- **Logs eines Containers anzeigen:**
  ```bash
  docker logs <container-id>
  ```
  Beispiel:
  ```bash
  docker logs my-container
  ```

- **Echtzeit-Logs mit `-f` anzeigen (folgen):**
  ```bash
  docker logs -f <container-id>
  ```
  Dieser Befehl zeigt die Logs in Echtzeit an und folgt neuen Einträgen, ähnlich wie `tail -f`.

- **Begrenzung der Anzahl der anzuzeigenden Logs:**
  - **Letzten `n` Zeilen anzeigen:**
    ```bash
    docker logs --tail <number-of-lines> <container-id>
    ```
    Beispiel:
    ```bash
    docker logs --tail 100 my-container
    ```
  - **Logs seit einem bestimmten Zeitpunkt anzeigen:**
    ```bash
    docker logs --since <timestamp> <container-id>
    ```
    Beispiel:
    ```bash
    docker logs --since 2023-06-29T00:00:00 my-container
    ```

- **Logs mit Zeitstempeln anzeigen:**
  ```bash
  docker logs -t <container-id>
  ```

#### 2. Konfiguration von Log-Driver

Docker unterstützt verschiedene Log-Driver, die definieren, wie und wohin Logs geschrieben werden. Standardmäßig verwendet Docker den `json-file`-Log-Driver. Hier sind einige Schritte zur Konfiguration von Log-Driver:

- **Verfügbare Log-Driver:**
  - `json-file`: Speichert Logs als JSON-Dateien auf dem Host.
  - `syslog`: Sendet Logs an den Syslog-Dienst.
  - `journald`: Sendet Logs an `systemd` journald.
  - `gelf`: Sendet Logs an einen Graylog Extended Log Format (GELF) Endpunkt.
  - `fluentd`: Sendet Logs an einen Fluentd-Logsammler.
  - `awslogs`: Sendet Logs an Amazon CloudWatch.
  - `splunk`: Sendet Logs an einen Splunk-Server.

- **Einen Log-Driver für einen Container festlegen:**
  ```bash
  docker run --log-driver=<driver-name> <image-name>
  ```
  Beispiel:
  ```bash
  docker run --log-driver=syslog my-container
  ```

- **Globale Konfiguration des Log-Drivers:**
  Um den Standard-Log-Driver für alle Container zu ändern, bearbeiten Sie die Docker-Daemon-Konfigurationsdatei (`/etc/docker/daemon.json`):
  ```json
  {
    "log-driver": "syslog",
    "log-opts": {
      "syslog-address": "tcp://192.168.0.42:123"
    }
  }
  ```
  Nach dem Ändern der Datei müssen Sie den Docker-Daemon neu starten:
  ```bash
  sudo systemctl restart docker
  ```

- **Log-Optionen konfigurieren:**
  Sie können zusätzliche Optionen für den gewählten Log-Driver angeben, wie im obigen Beispiel gezeigt. Weitere Optionen finden Sie in der [Docker-Dokumentation](https://docs.docker.com/config/containers/logging/configure/).

#### Fazit

Die richtige Verwaltung und Analyse von Logs ist entscheidend für die Wartung und Fehlerbehebung Ihrer Docker-Container. Mit dem `docker logs`-Befehl können Sie schnell auf Logs zugreifen, und durch die Konfiguration von Log-Driver können Sie Ihre Logs effizienter und nach Ihren Bedürfnissen verwalten. Nutzen Sie diese Werkzeuge, um Ihre Container besser zu überwachen und zu debuggen.

### Docker Compose Tutorial #18 - Logs ansehen

In diesem Tutorial erfahren Sie, wie Sie Logs von Docker-Containern in einem Docker-Compose-Setup abrufen und analysieren können. Logs sind ein wesentlicher Bestandteil beim Debuggen und Überwachen von Anwendungen. Docker-Compose bietet mehrere Möglichkeiten, um Logs aus Containern zu extrahieren und zu verwalten. Wir werden uns die Verwendung des `docker-compose logs`-Befehls und die Konfiguration von Log-Driver in Docker-Compose-Dateien ansehen.

#### 1. Verwendung von `docker-compose logs`

Der `docker-compose logs`-Befehl wird verwendet, um die Logs eines oder mehrerer Dienste in einem Compose-Setup anzuzeigen. Hier sind die grundlegenden Schritte zur Verwendung dieses Befehls:

- **Logs aller Dienste anzeigen:**
  ```bash
  docker-compose logs
  ```

- **Logs eines bestimmten Dienstes anzeigen:**
  ```bash
  docker-compose logs <service-name>
  ```
  Beispiel:
  ```bash
  docker-compose logs web
  ```

- **Echtzeit-Logs mit `-f` anzeigen (folgen):**
  ```bash
  docker-compose logs -f
  ```
  Dieser Befehl zeigt die Logs in Echtzeit an und folgt neuen Einträgen, ähnlich wie `tail -f`.

- **Begrenzung der Anzahl der anzuzeigenden Logs:**
  - **Letzten `n` Zeilen anzeigen:**
    ```bash
    docker-compose logs --tail <number-of-lines>
    ```
    Beispiel:
    ```bash
    docker-compose logs --tail 100
    ```

- **Logs mit Zeitstempeln anzeigen:**
  ```bash
  docker-compose logs -t
  ```

#### 2. Konfiguration von Log-Driver in Docker-Compose

Docker-Compose unterstützt die Konfiguration von Log-Drivern auf Dienstebene. Hier sind die Schritte zur Konfiguration von Log-Drivern in der `docker-compose.yml`-Datei:

- **Verfügbare Log-Driver:**
  - `json-file`: Speichert Logs als JSON-Dateien auf dem Host.
  - `syslog`: Sendet Logs an den Syslog-Dienst.
  - `journald`: Sendet Logs an `systemd` journald.
  - `gelf`: Sendet Logs an einen Graylog Extended Log Format (GELF) Endpunkt.
  - `fluentd`: Sendet Logs an einen Fluentd-Logsammler.
  - `awslogs`: Sendet Logs an Amazon CloudWatch.
  - `splunk`: Sendet Logs an einen Splunk-Server.

- **Einen Log-Driver für einen Dienst festlegen:**
  ```yaml
  version: '3.8'
  services:
    web:
      image: my-web-image
      logging:
        driver: syslog
        options:
          syslog-address: "tcp://192.168.0.42:123"
  ```

- **Globale Konfiguration des Log-Drivers:**
  Um den Standard-Log-Driver für alle Dienste in einer Docker-Compose-Datei zu ändern, können Sie die folgenden Einstellungen im Root-Level Ihrer `docker-compose.yml`-Datei hinzufügen:
  ```yaml
  version: '3.8'
  services:
    web:
      image: my-web-image
  logging:
    driver: syslog
    options:
      syslog-address: "tcp://192.168.0.42:123"
  ```

- **Log-Optionen konfigurieren:**
  Sie können zusätzliche Optionen für den gewählten Log-Driver angeben, wie im obigen Beispiel gezeigt. Weitere Optionen finden Sie in der [Docker-Compose-Dokumentation](https://docs.docker.com/compose/compose-file/compose-file-v3/#logging).

#### Fazit

Die richtige Verwaltung und Analyse von Logs ist entscheidend für die Wartung und Fehlerbehebung Ihrer Docker-Container. Mit dem `docker-compose logs`-Befehl können Sie schnell auf Logs zugreifen, und durch die Konfiguration von Log-Drivern können Sie Ihre Logs effizienter und nach Ihren Bedürfnissen verwalten. Nutzen Sie diese Werkzeuge, um Ihre Container besser zu überwachen und zu debuggen.