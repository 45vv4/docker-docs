# Docker unter Linux installieren: Eine Schritt-für-Schritt-Anleitung

In diesem Tutorial lernen Sie, wie Sie Docker auf einem Linux-System installieren. Wir behandeln die Installation über das offizielle Docker-Repository, das Hinzufügen des Docker GPG-Schlüssels und die Konfiguration des Docker-Daemons. Folgen Sie diesen Schritten, um Docker auf Ihrem Linux-Computer zum Laufen zu bringen.

## Schritt 1: System aktualisieren
Bevor Sie Docker installieren, stellen Sie sicher, dass Ihr System auf dem neuesten Stand ist.

```sh
sudo apt-get update
sudo apt-get upgrade
```

## Schritt 2: Abhängigkeiten installieren
Installieren Sie die notwendigen Pakete, um HTTPS verwenden zu können:

```sh
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common

# command morpheus
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common gnupg-agent

```

## Schritt 3: Docker GPG-Schlüssel hinzufügen
Fügen Sie den offiziellen Docker GPG-Schlüssel zu Ihrem System hinzu:

```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Ja, der Befehl `sudo apt-key fingerprint 0EBFCD88` ist korrekt. Dieser Befehl zeigt den Fingerabdruck des spezifischen GPG-Schlüssels mit der ID `0EBFCD88` an, der für Docker verwendet wird.

Hier ist die genaue Verwendung:

```sh
# command morpheus 
sudo apt-key fingerprint 0EBFCD88
```

Dieser Befehl gibt den vollständigen Fingerabdruck und weitere Details des Docker GPG-Schlüssels aus. Es ist eine nützliche Methode, um die Integrität und Authentizität des Schlüssels zu überprüfen, den Sie hinzugefügt haben.

Um die Details des hinzugefügten GPG-Schlüssels anzuzeigen, können Sie den folgenden Befehl verwenden:

```sh
sudo apt-key list
```

Dieser Befehl zeigt alle GPG-Schlüssel an, die derzeit im APT-Schlüsselring gespeichert sind, einschließlich des Docker GPG-Schlüssels, den Sie hinzugefügt haben.

Wenn Sie spezifische Informationen über den Docker-Schlüssel anzeigen möchten, können Sie den Fingerabdruck des Schlüssels aus der Liste der Schlüssel extrahieren und dann mit dem folgenden Befehl die Details anzeigen:

```sh
sudo apt-key finger <fingerprint>
```

Ersetzen Sie `<fingerprint>` durch den tatsächlichen Fingerabdruck des Schlüssels, den Sie in der Ausgabe von `sudo apt-key list` gefunden haben.

Beispiel:

1. Listen Sie alle Schlüssel auf:

    ```sh
    sudo apt-key list
    ```

2. Suchen Sie den Fingerabdruck des Docker-Schlüssels in der Ausgabe.
3. Zeigen Sie die Details des Schlüssels mit dem Fingerabdruck an:

    ```sh
    sudo apt-key finger <fingerprint>
    ```

Durch diese Befehle können Sie die Form und die Details des erstellten Schlüssels anzeigen.

## Schritt 4: Docker-Repository hinzufügen
Fügen Sie das Docker-Repository zu den APT-Quellen hinzu:

```sh
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

## Schritt 5: APT-Paketindex aktualisieren
Aktualisieren Sie den APT-Paketindex, um die neuen Docker-Repository-Pakete zu berücksichtigen:

```sh
sudo apt-get update
```

## Schritt 6: Docker installieren
Installieren Sie Docker CE (Community Edition):

```sh
sudo apt-get install docker-ce

# command morpheus
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## Schritt 7: Überprüfen Sie die Docker-Installation
Überprüfen Sie, ob Docker erfolgreich installiert wurde, indem Sie die Docker-Version abrufen:

```sh
docker --version
```

## Schritt 8: Docker-Daemon konfigurieren (optional)
Sie können den Docker-Daemon konfigurieren, indem Sie die Konfigurationsdatei bearbeiten. Öffnen Sie die Datei mit einem Texteditor:

```sh
sudo nano /etc/docker/daemon.json
```

Fügen Sie Ihre gewünschten Konfigurationseinstellungen hinzu. Zum Beispiel:

```json
{
  "storage-driver": "overlay2"
}
```

Speichern und schließen Sie die Datei. Starten Sie den Docker-Daemon neu, um die Änderungen zu übernehmen:

```sh
sudo systemctl restart docker
```

## Schritt 9: Docker als Nicht-Root-Benutzer verwenden (optional)
Um Docker-Befehle ohne `sudo` auszuführen, fügen Sie Ihren Benutzer zur Docker-Gruppe hinzu:

```sh
sudo usermod -aG docker $USER
```

Loggen Sie sich aus und wieder ein, damit die Gruppenänderungen wirksam werden.

## Schritt 10: Testen Sie Docker
Testen Sie die Docker-Installation, indem Sie ein einfaches Docker-Container-Image ausführen:

```sh
docker run hello-world
```

Wenn Sie die obige Ausgabe sehen, bedeutet dies, dass Docker erfolgreich installiert und konfiguriert wurde.

# Fazit
Sie haben Docker erfolgreich auf Ihrem Linux-System installiert und konfiguriert. Jetzt können Sie Docker-Container erstellen und verwalten. Für weitere Informationen und fortgeschrittene Konfigurationen besuchen Sie die [offizielle Docker-Dokumentation](https://docs.docker.com/).