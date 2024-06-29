# Docker Tutorial #2 - Wie Docker arbeitet

In diesem Kapitel wird die Funktionsweise von Docker detailliert beschrieben. Wir werden die Docker-Architektur erläutern, einschließlich der Hauptkomponenten wie Docker Daemon, Docker Client, Images und Container. Ziel ist es, ein umfassendes Verständnis für die wichtigsten Docker-Komponenten und deren Zusammenspiel zu vermitteln.

![Wie Docker arbeitet](./images/02_Wie%20Docker%20arbeitet.jpg)

## Docker Architektur

Die Docker-Architektur besteht aus mehreren Schlüsselkomponenten, die zusammenarbeiten, um eine effiziente und skalierbare Container-Verwaltung zu ermöglichen. Zu den wichtigsten Komponenten gehören:

1. **Docker Daemon (dockerd)**
2. **Docker Client**
3. **Docker Images**
4. **Docker Container**

### 1. Docker Daemon (dockerd)

Der Docker Daemon, oft als `dockerd` bezeichnet, ist der zentrale Hintergrunddienst, der für das Erstellen, Verwalten und Überwachen von Docker-Containern verantwortlich ist. Der Daemon empfängt Anfragen vom Docker Client und führt diese aus. Wichtige Funktionen des Docker Daemon umfassen:

- Verwaltung von Docker-Containern (Starten, Stoppen, Neustarten)
- Erstellen und Verwalten von Docker-Images
- Netzwerk- und Speicherverwaltung für Container
- Bereitstellung von APIs für die Interaktion mit Docker

### 2. Docker Client

Der Docker Client ist die Benutzeroberfläche für Docker. Es handelt sich um ein Kommandozeilen-Tool, das Benutzer verwenden, um mit dem Docker Daemon zu interagieren. Typische Befehle, die über den Docker Client ausgeführt werden, sind:

- `docker build`: Zum Erstellen eines Docker-Images aus einem Dockerfile
- `docker run`: Zum Starten eines neuen Containers aus einem Docker-Image
- `docker stop`: Zum Stoppen eines laufenden Containers
- `docker ps`: Zum Auflisten aller laufenden Container

### 3. Docker Images

Docker Images sind unveränderliche Vorlagen, die alle notwendigen Anweisungen und Dateien enthalten, um einen Container zu erstellen. Ein Image kann aus mehreren Schichten (Layers) bestehen, wobei jede Schicht Änderungen gegenüber der vorherigen speichert. Images werden in der Regel aus einem Dockerfile erstellt, das eine Reihe von Anweisungen enthält, wie das Image gebaut werden soll. Wichtige Aspekte von Docker Images sind:

- Images sind schreibgeschützt.
- Sie können in öffentlichen oder privaten Repositories gespeichert werden, wie Docker Hub.
- Images können Versionen haben, die durch Tags gekennzeichnet sind.

### 4. Docker Container

Ein Docker Container ist eine Instanz eines Docker Images. Container sind isolierte Umgebungen, die auf demselben Betriebssystemkern laufen, aber ihre eigenen Dateisysteme, Prozesse und Netzwerkschnittstellen haben. Container bieten eine portable und konsistente Umgebung für die Ausführung von Anwendungen. Wichtige Merkmale von Docker Containern sind:

- Leichtgewichtig und schnell zu starten
- Isoliert von anderen Containern und dem Host-System
- Sie können einfach gestoppt, gestartet und entfernt werden

## Zusammenspiel der Komponenten

Das Zusammenspiel der Docker-Komponenten lässt sich wie folgt beschreiben:

1. **Erstellen eines Images:** Der Benutzer schreibt ein Dockerfile und verwendet den Befehl `docker build`, um ein Docker-Image zu erstellen. Der Docker Client sendet diese Anfrage an den Docker Daemon, der das Image basierend auf den Anweisungen im Dockerfile erstellt.
2. **Speichern und Abrufen von Images:** Das erstellte Image kann in einem Docker-Repository, wie Docker Hub, gespeichert werden. Andere Benutzer können das Image dann mit `docker pull` abrufen.
3. **Starten eines Containers:** Mit dem Befehl `docker run` startet der Benutzer einen Container aus einem Docker-Image. Der Docker Daemon erstellt den Container und sorgt dafür, dass er isoliert läuft.
4. **Verwalten von Containern:** Der Benutzer kann Container mit Befehlen wie `docker stop`, `docker start` und `docker rm` verwalten. Diese Befehle werden vom Docker Client an den Docker Daemon weitergeleitet, der die entsprechenden Aktionen ausführt.

Zusammen ermöglichen diese Komponenten eine effiziente und flexible Verwaltung von Containern, die eine konsistente Umgebung für die Entwicklung, das Testen und den Betrieb von Anwendungen bieten. Docker erleichtert die Bereitstellung und Skalierung von Anwendungen erheblich, indem es die Komplexität der Verwaltung von Anwendungsabhängigkeiten und -umgebungen reduziert.