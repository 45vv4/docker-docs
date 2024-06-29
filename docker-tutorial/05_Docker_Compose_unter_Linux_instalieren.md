### Docker Compose unter Linux installieren

Docker Compose ist ein leistungsstarkes Werkzeug zum Definieren und Ausführen von Multi-Container Docker-Anwendungen. In dieser Anleitung zeigen wir Ihnen, wie Sie Docker Compose auf einem Linux-System installieren können.

[docker-compose releases: click here](https://github.com/docker/compose/releases)

#### Schritt 1: System aktualisieren

Stellen Sie sicher, dass Ihr System auf dem neuesten Stand ist, indem Sie die folgenden Befehle ausführen:

```bash
sudo apt update
sudo apt upgrade -y
```

#### Schritt 2: Docker installieren

Falls Docker noch nicht installiert ist, folgen Sie diesen Schritten zur Installation:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install docker-ce -y
```

Überprüfen Sie die Docker-Installation:

```bash
sudo systemctl status docker
```

#### Schritt 3: Docker Compose herunterladen

Verwenden Sie `curl`, um die neueste Version von Docker Compose herunterzuladen. Besuchen Sie die [GitHub-Seite von Docker Compose](https://github.com/docker/compose/releases) und überprüfen Sie die neueste Version.

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

#### Schritt 4: Docker Compose ausführbar machen

Geben Sie der heruntergeladenen Datei die entsprechenden Berechtigungen:

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

#### Schritt 5: Installation überprüfen

Überprüfen Sie die Installation, indem Sie die Version von Docker Compose abrufen:

```bash
docker-compose --version
```

Wenn alles korrekt installiert ist, sollten Sie eine Ausgabe wie diese sehen:

```
docker-compose version 2.16.0, build ...
```

#### Schritt 6: Optional - Docker Compose Autocomplete einrichten

Um die Autovervollständigung für Docker Compose zu aktivieren, führen Sie folgende Befehle aus:

```bash
sudo curl -L https://raw.githubusercontent.com/docker/compose/1.29.2/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
```

Laden Sie das neue Autocomplete-Skript:

```bash
source /etc/bash_completion.d/docker-compose
```

### Fazit

Mit diesen Schritten haben Sie Docker Compose erfolgreich auf Ihrem Linux-System installiert. Sie können nun Docker Compose verwenden, um Ihre Multi-Container-Anwendungen zu definieren und zu verwalten. Viel Erfolg beim Arbeiten mit Docker Compose!