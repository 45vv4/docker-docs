## Docker Tutorial #5 - Docker unter Mac installieren

In diesem Kapitel zeigen wir Ihnen, wie Docker Desktop auf einem Mac installiert wird. Wir decken die erforderlichen Systemanforderungen ab und führen Sie durch die Installation und Konfiguration.

### Systemanforderungen

Bevor wir mit der Installation beginnen, stellen Sie sicher, dass Ihr Mac die folgenden Systemanforderungen erfüllt:

1. **Betriebssystem**: macOS 10.15 oder neuer.
2. **Hardware**: Ein Mac mit Intel- oder Apple-Silicon-Chip.
3. **RAM**: Mindestens 4 GB RAM (8 GB oder mehr empfohlen).
4. **Virtuelle Maschinen**: Docker Desktop verwendet HyperKit (für Intel Macs) oder Apple Hypervisor Framework (für Apple Silicon Macs), daher ist keine separate Virtualisierungssoftware erforderlich.

### Schritt 1: Docker Desktop herunterladen

1. Öffnen Sie Ihren bevorzugten Webbrowser und navigieren Sie zur [Docker Desktop für Mac-Seite](https://www.docker.com/products/docker-desktop).
2. Klicken Sie auf die Schaltfläche „Download für Mac“, um die Installationsdatei herunterzuladen. 

### Schritt 2: Docker Desktop installieren

1. Öffnen Sie die heruntergeladene `.dmg`-Datei.
2. Ziehen Sie das Docker-Symbol in den Ordner „Programme“, um Docker Desktop zu installieren.
3. Öffnen Sie den Ordner „Programme“ und starten Sie Docker Desktop.

### Schritt 3: Docker Desktop konfigurieren

1. Nach dem ersten Start von Docker Desktop werden Sie möglicherweise aufgefordert, Docker die Berechtigung zu erteilen, Systemerweiterungen zu installieren und Änderungen vorzunehmen. Bestätigen Sie dies und geben Sie Ihr Administratorpasswort ein.
2. Docker Desktop wird im Hintergrund ausgeführt und das Docker-Symbol erscheint in der Menüleiste.

### Schritt 4: Docker Desktop testen

1. Öffnen Sie das Terminal.
2. Geben Sie `docker --version` ein und drücken Sie die Eingabetaste, um zu überprüfen, ob Docker korrekt installiert ist.
3. Führen Sie `docker run hello-world` aus, um einen Test-Container zu starten und sicherzustellen, dass Docker funktioniert.

### Häufige Probleme und Lösungen

- **Fehlermeldung „Docker läuft nicht“**: Stellen Sie sicher, dass Docker Desktop im Hintergrund läuft und das Docker-Symbol in der Menüleiste sichtbar ist.
- **Performance-Probleme**: Erhöhen Sie die Docker Desktop-zugewiesenen Ressourcen über die Einstellungen (z. B. mehr CPU und RAM zuweisen).

### Zusammenfassung

Sie haben erfolgreich Docker Desktop auf Ihrem Mac installiert und konfiguriert. Docker ist jetzt einsatzbereit und Sie können Container erstellen und verwalten. Im nächsten Kapitel werden wir die grundlegende Nutzung von Docker-Containern und -Images behandeln.

Falls Sie Fragen oder Probleme haben, können Sie die [offizielle Docker-Dokumentation](https://docs.docker.com/desktop/mac/install/) konsultieren oder sich an die Docker-Community wenden.