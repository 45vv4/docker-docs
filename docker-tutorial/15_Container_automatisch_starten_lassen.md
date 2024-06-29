[Docker Tutorial #15 - Container automatisch starten lassen (Unter Linux)](https://www.youtube.com/watch?v=KXyD4K8ct1o&list=PLNmsVeXQZj7oea6IDCLzpKe5XfLmWCwgr&index=17)

## Das folgende Beispiel ist mit docker-compose:

Um Docker-Container automatisch beim Systemstart zu starten, können wir Docker-Compose und systemd-Units verwenden. Hier ist eine Schritt-für-Schritt-Anleitung, wie man dies erreicht:

### Schritt 1: Docker-Compose Datei erstellen
Erstellen Sie eine `docker-compose.yml` Datei in Ihrem Projektverzeichnis. Diese Datei definiert die Container, die Sie verwenden möchten.

Beispiel einer `docker-compose.yml` Datei:
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: example
```

### Schritt 2: Systemd-Unit Datei erstellen
Erstellen Sie eine systemd-Unit-Datei für Ihren Docker-Compose-Stack. Diese Datei sollte im Verzeichnis `/etc/systemd/system` gespeichert werden.

Erstellen Sie die Datei `/etc/systemd/system/docker-compose-app.service` mit folgendem Inhalt:

```ini
[Unit]
Description=Docker Compose Application Service
Requires=docker.service
After=docker.service

[Service]
Type=oneshot
RemainAfterExit=yes
WorkingDirectory=/pfad/zu/ihrem/projekt
ExecStart=/usr/local/bin/docker-compose up -d
ExecStop=/usr/local/bin/docker-compose down
TimeoutStartSec=0

[Install]
WantedBy=multi-user.target
```

### Schritt 3: Systemd-Unit Datei aktivieren
Aktivieren Sie die systemd-Unit-Datei, damit sie beim Systemstart ausgeführt wird.

```sh
sudo systemctl enable docker-compose-app
```

### Schritt 4: Docker-Compose Stack starten
Starten Sie den Docker-Compose-Stack manuell, um sicherzustellen, dass alles korrekt konfiguriert ist.

```sh
cd /pfad/zu/ihrem/projekt
docker-compose up -d
```

### Schritt 5: Systemd-Unit Datei testen
Überprüfen Sie, ob die systemd-Unit-Datei korrekt funktioniert, indem Sie den Service starten und stoppen.

```sh
sudo systemctl start docker-compose-app
sudo systemctl status docker-compose-app
```

Wenn alles richtig konfiguriert ist, sollten Ihre Docker-Container nun automatisch beim Systemstart hochfahren. 

### Zusätzliche Hinweise
- Stellen Sie sicher, dass Docker und Docker-Compose korrekt installiert sind und dass der Pfad zu Docker-Compose in der Unit-Datei (`/usr/local/bin/docker-compose`) korrekt ist.
- Überprüfen Sie die Rechte und stellen Sie sicher, dass die systemd-Unit-Datei die richtigen Berechtigungen hat.

Mit diesen Schritten können Sie sicherstellen, dass Ihre Docker-Container automatisch beim Systemstart gestartet werden, was besonders nützlich für Produktionsumgebungen ist.