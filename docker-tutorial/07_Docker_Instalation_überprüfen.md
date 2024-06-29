### Docker Tutorial #7 - Die Installation überprüfen

Nachdem Docker auf deinem System installiert ist, ist es wichtig zu überprüfen, ob die Installation erfolgreich war und Docker korrekt funktioniert. Hier sind die Schritte, um die Installation von Docker zu überprüfen:

#### 1. Überprüfung der Docker-Version

Öffne ein Terminal oder eine Eingabeaufforderung und gib den folgenden Befehl ein, um die installierte Docker-Version zu überprüfen:

```sh
docker --version
```

Du solltest eine Ausgabe erhalten, die die installierte Docker-Version anzeigt, etwa so:

```sh
Docker version 20.10.7, build f0df350
```

#### 2. Überprüfung, ob der Docker-Daemon läuft

Um zu überprüfen, ob der Docker-Daemon läuft, kannst du den folgenden Befehl verwenden:

```sh
docker info
```

Dieser Befehl gibt eine Menge Informationen über deine Docker-Installation zurück, einschließlich der Anzahl der Container und Images sowie Informationen zur Docker-Engine und zum Speicher.

#### 3. Ausführen eines Test-Containers

Der einfachste Weg, um sicherzustellen, dass Docker korrekt funktioniert, besteht darin, einen Test-Container auszuführen. Wir können den offiziellen `hello-world`-Container verwenden, um dies zu tun. Gib im Terminal folgenden Befehl ein:

```sh
docker run hello-world
```

Wenn Docker korrekt installiert und konfiguriert ist, solltest du eine Ausgabe ähnlich dieser sehen:

```sh
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
```

#### Fehlerbehebung

Falls einer der obigen Schritte nicht funktioniert, könnte es an verschiedenen Problemen liegen:

- **Docker-Daemon läuft nicht**: Stelle sicher, dass der Docker-Daemon läuft. Auf Linux-Systemen kannst du dies mit `sudo systemctl start docker` starten. Auf Windows und Mac kannst du sicherstellen, dass die Docker Desktop-Anwendung läuft.
- **Berechtigungsprobleme**: Auf einigen Systemen kann es erforderlich sein, Docker-Befehle mit `sudo` auszuführen, z. B. `sudo docker run hello-world`.

#### Zusammenfassung

Die Überprüfung der Docker-Installation ist ein wichtiger Schritt, um sicherzustellen, dass alles korrekt funktioniert. Die oben genannten Schritte helfen dir dabei, sicherzustellen, dass Docker korrekt installiert ist und einsatzbereit ist. 

Falls du weitere Unterstützung benötigst, gibt es eine Vielzahl an Ressourcen und Dokumentationen auf der [offiziellen Docker-Website](https://docs.docker.com/get-started/).