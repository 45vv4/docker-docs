# Docker Tutorial Dokumentation

## Inhaltsverzeichnis

1. [Docker Tutorial #1 - Warum ihr Docker braucht!](#docker-tutorial-1---warum-ihr-docker-braucht)
2. [Virtuelle Maschinen vs Container / Docker](#virtuelle-maschinen-vs-container--docker)
3. [Docker Tutorial #2 - Wie Docker arbeitet](#docker-tutorial-2---wie-docker-arbeitet)
4. [Docker Tutorial #3 - Docker unter Linux installieren](#docker-tutorial-3---docker-unter-linux-installieren)
5. [Docker Tutorial #4 - Docker unter Windows installieren](#docker-tutorial-4---docker-unter-windows-installieren)
6. [Docker Tutorial #5 - Docker unter Mac installieren](#docker-tutorial-5---docker-unter-mac-installieren)
7. [Nested VMs sind meistens eine schlechte Idee](#nested-vms-sind-meistens-eine-schlechte-idee)
8. [Docker Tutorial #6 - Docker Compose unter Linux installieren](#docker-tutorial-6---docker-compose-unter-linux-installieren)
9. [Docker Tutorial #7 - Die Installation überprüfen](#docker-tutorial-7---die-installation-überprüfen)
10. [Docker Tutorial #8 - Eine Busybox starten](#docker-tutorial-8---eine-busybox-starten)
11. [Docker Tutorial #9 - Befehle im inneren des Containers ausführen](#docker-tutorial-9---befehle-im-inneren-des-containers-ausführen)
12. [Docker Tutorial #10 - WebApps und Port Mapping](#docker-tutorial-10---webapps-und-port-mapping)
13. [Docker Tutorial #11 - Der Detached Modus](#docker-tutorial-11---der-detached-modus)
14. [Docker Tutorial #12 - Eine Shell im Detached Mode erlangen](#docker-tutorial-12---eine-shell-im-detached-mode-erlangen)
15. [Docker Tutorial #13 - Dateien an Container übergeben](#docker-tutorial-13---dateien-an-container-übergeben)
16. [Docker Tutorial #14 - Container stoppen, Löschen von Images und Containern](#docker-tutorial-14---container-stoppen-löschen-von-images-und-containern)
17. [Docker Tutorial #15 - Container automatisch starten lassen](#docker-tutorial-15---container-automatisch-starten-lassen)
18. [Docker Tutorial #16 - Statistiken der laufenden Container](#docker-tutorial-16---statistiken-der-laufenden-container)
19. [Docker Tutorial #17 - Die Ressourcen eines Containers limitieren](#docker-tutorial-17---die-ressourcen-eines-containers-limitieren)
20. [Docker Tutorial #18 - Logs ansehen](#docker-tutorial-18---logs-ansehen)
21. [Docker Tutorial #19 - In eine Datei loggen](#docker-tutorial-19---in-eine-datei-loggen)
22. [Docker Tutorial #20 - Dockerfiles](#docker-tutorial-20---dockerfiles)
23. [Docker Tutorial #21 - Dockerfiles builden und starten](#docker-tutorial-21---dockerfiles-builden-und-starten)
24. [Docker Tutorial #22 - Images auf Docker Hub teilen](#docker-tutorial-22---images-auf-docker-hub-teilen)
25. [Docker Tutorial #23 - Environment Variablen](#docker-tutorial-23---environment-variablen)
26. [Docker Tutorial #24 - Python Deployment mit Docker](#docker-tutorial-24---python-deployment-mit-docker)
27. [Docker Tutorial #25 - Nodejs Deployment mit Docker](#docker-tutorial-25---nodejs-deployment-mit-docker)
28. [Docker Tutorial #26 - Ein Email Server mit MailCow](#docker-tutorial-26---ein-email-server-mit-mailcow)
29. [Docker Tutorial #27 - Wordpress mit Docker installieren](#docker-tutorial-27---wordpress-mit-docker-installieren)
30. [Docker Tutorial #28 - Eine eigene Cloud mit Nextcloud](#docker-tutorial-28---eine-eigene-cloud-mit-nextcloud)
31. [Docker Tutorial #29 - Mehr Optionen in Docker Compose Files](#docker-tutorial-29---mehr-optionen-in-docker-compose-files)
32. [Docker Tutorial #30 - Swarms](#docker-tutorial-30---swarms)
33. [Docker Tutorial #31 - Docker Machine auf Linux installieren](#docker-tutorial-31---docker-machine-auf-linux-installieren)
34. [Docker Tutorial #32 - Lokale virtuelle Maschinen erstellen](#docker-tutorial-32---lokale-virtuelle-maschinen-erstellen)
35. [Docker Tutorial #33 - Zusätzliche Informationen über die VMs](#docker-tutorial-33---zusätzliche-informationen-über-die-vms)
36. [Docker Tutorial #34 - Einen Swarm erstellen](#docker-tutorial-34---einen-swarm-erstellen)
37. [Docker Tutorial #35 - Eine App im Swarm hosten](#docker-tutorial-35---eine-app-im-swarm-hosten)
38. [Docker Tutorial #36 - Den Stack beenden, den Swarm verlassen](#docker-tutorial-36---den-stack-beenden-den-swarm-verlassen)
39. [Docker Tutorial #37 - Ein Image nur auf dem Manager starten](#docker-tutorial-37---ein-image-nur-auf-dem-manager-starten)
40. [Docker Tutorial #38 - Einen einzelnen Service im Cluster veröffentlichen](#docker-tutorial-38---einen-einzeln-service-im-cluster-veröffentlichen)
41. [Docker Tutorial #39 - Services update](#docker-tutorial-39---services-update)
42. [Docker Tutorial #40 - Letzte Worte](#docker-tutorial-40---letzte-worte)
43. [Docker Tutorial Bonus - Joomla mit Docker aufsetzen](#docker-tutorial-bonus---joomla-mit-docker-aufsetzen)
44. [Docker Tutorial Bonus - Docker Compose Dateiformat Version](#docker-tutorial-bonus---docker-compose-dateiformat-version)

Natürlich, hier sind die Nachteile von Docker, die wir im obigen Text ergänzen können:

# Docker Tutorial #1 - Warum ihr Docker braucht!

## Einführung

In der modernen Softwareentwicklung stehen Entwickler und Systemadministratoren vor zahlreichen Herausforderungen. Unterschiedliche Entwicklungsumgebungen, komplexe Bereitstellungsprozesse und die Notwendigkeit, Anwendungen in verschiedenen Umgebungen auszuführen, erfordern flexible und konsistente Lösungen. Hier kommt Docker ins Spiel. Docker revolutioniert die Art und Weise, wie Software entwickelt, bereitgestellt und ausgeführt wird, und bietet zahlreiche Vorteile gegenüber traditionellen virtuellen Maschinen. Allerdings gibt es auch einige Nachteile, die berücksichtigt werden sollten.

## Was ist Docker?

Docker ist eine Open-Source-Plattform, die es Entwicklern ermöglicht, Anwendungen in Containern zu verpacken, zu verteilen und auszuführen. Container sind leichtgewichtige, portable und isolierte Umgebungen, die alle notwendigen Komponenten einer Anwendung enthalten, einschließlich Bibliotheken und Abhängigkeiten. Dies stellt sicher, dass die Anwendung in jeder Umgebung gleich läuft, unabhängig davon, wo sie ausgeführt wird.

## Vorteile von Docker

### 1. Konsistente Entwicklungsumgebung

Einer der größten Vorteile von Docker ist die Möglichkeit, eine konsistente Entwicklungsumgebung zu schaffen. Entwickler können sicherstellen, dass die Anwendung auf ihrem lokalen Rechner genauso funktioniert wie in der Produktionsumgebung. Docker-Container enthalten alle erforderlichen Abhängigkeiten, was das Problem der „Es funktioniert auf meinem Rechner“-Ausreden eliminiert.

### 2. Einfache Bereitstellung

Docker vereinfacht den Bereitstellungsprozess erheblich. Anstatt komplizierte Installationsanweisungen zu befolgen oder verschiedene Konfigurationsprobleme zu lösen, können Entwickler und Systemadministratoren einfach den Container auf dem Zielsystem ausführen. Da Container isoliert sind, gibt es keine Konflikte mit anderen Anwendungen oder Abhängigkeiten auf dem Host-System.

### 3. Effiziente Ressourcennutzung

Im Vergleich zu traditionellen virtuellen Maschinen sind Docker-Container viel ressourceneffizienter. Container teilen sich den Kernel des Host-Betriebssystems, was zu einem geringeren Overhead führt. Dies ermöglicht es, mehr Container auf demselben Host auszuführen und die Hardware-Ressourcen optimal zu nutzen.

### 4. Skalierbarkeit

Docker erleichtert die Skalierung von Anwendungen. Container können schnell gestartet oder gestoppt werden, was eine flexible Reaktion auf Laständerungen ermöglicht. Tools wie Docker Swarm und Kubernetes bieten zusätzliche Funktionen zur Orchestrierung und Verwaltung von Container-Clustern, was die Skalierbarkeit weiter verbessert.

### 5. Unterstützung für Continuous Integration und Continuous Deployment (CI/CD)

Docker spielt eine entscheidende Rolle in modernen CI/CD-Pipelines. Containerisierte Anwendungen können leicht getestet und in verschiedene Stufen der Pipeline bereitgestellt werden. Dies beschleunigt den Entwicklungszyklus und verbessert die Qualität der Software.

### 6. Portabilität

Docker-Container sind extrem portabel. Sie können auf jedem System ausgeführt werden, das Docker unterstützt, sei es ein lokaler Entwicklungsrechner, ein Server im Rechenzentrum oder eine Cloud-Umgebung. Dies erleichtert den Wechsel zwischen verschiedenen Umgebungen und Anbietern.

## Nachteile von Docker

### 1. Komplexität der Orchestrierung

Während Docker selbst relativ einfach zu bedienen ist, kann die Verwaltung einer großen Anzahl von Containern komplex werden. Tools wie Kubernetes und Docker Swarm bieten zwar Lösungen zur Orchestrierung, bringen jedoch zusätzliche Komplexität und Lernkurven mit sich.

### 2. Sicherheitsrisiken

Container teilen sich den Kernel des Host-Betriebssystems, was potenzielle Sicherheitsrisiken mit sich bringt. Ein Sicherheitsproblem im Kernel kann alle Container auf demselben Host betreffen. Es ist daher wichtig, Sicherheitspraktiken zu befolgen und Container regelmäßig zu aktualisieren.

### 3. Persistente Daten

Das Management von persistenten Daten in Docker-Containern kann herausfordernd sein. Da Container oft als flüchtige Einheiten betrachtet werden, erfordert das Speichern und Wiederherstellen von Daten besondere Aufmerksamkeit und die Nutzung von Volumes oder externen Speicherlösungen.

### 4. Netzwerk-Overhead

Der Netzwerk-Overhead bei der Kommunikation zwischen Containern und externen Systemen kann höher sein als bei herkömmlichen Anwendungen. Dies kann zu Leistungsproblemen führen, insbesondere in hochgradig verteilten Systemen.

### 5. Begrenzte Unterstützung für grafische Anwendungen

Docker ist hauptsächlich für serverseitige und command-line-basierte Anwendungen konzipiert. Die Unterstützung für grafische Anwendungen und Desktops ist begrenzt und oft kompliziert zu implementieren.

## Fazit

Docker bietet eine robuste Lösung für viele der Herausforderungen, mit denen Entwickler und Systemadministratoren konfrontiert sind. Mit Docker können sie konsistente Entwicklungsumgebungen schaffen, den Bereitstellungsprozess vereinfachen und von einer effizienteren Ressourcennutzung profitieren. Die Portabilität und Skalierbarkeit von Docker-Containern machen es zu einem unverzichtbaren Werkzeug in der modernen Softwareentwicklung. Allerdings sollten auch die Nachteile berücksichtigt und geeignete Maßnahmen ergriffen werden, um potenzielle Probleme zu minimieren.

In den folgenden Kapiteln dieses Tutorials werden wir uns eingehender mit der Verwendung von Docker beschäftigen und Schritt für Schritt zeigen, wie man Docker-Container erstellt, verwaltet und bereitstellt. Bleiben Sie dran!

# Virtuelle Maschinen vs Container / Docker

### 1. Architektur

**Virtuelle Maschinen (VMs):**
- **Hypervisor**: VMs laufen auf einem Hypervisor, der für die Virtualisierung der Hardware verantwortlich ist. Der Hypervisor kann entweder direkt auf der Hardware (Typ 1, z.B. VMware ESXi) oder auf einem Betriebssystem (Typ 2, z.B. VirtualBox) installiert sein.
- **Gastsystem**: Jede VM enthält ein vollständiges Betriebssystem (Gast-OS) sowie die notwendigen Bibliotheken und Anwendungen.
- **Isolierung**: VMs sind vollständig voneinander isoliert, da sie jeweils ihr eigenes Betriebssystem haben.

**Container:**
- **Container-Engine**: Container laufen auf einer Container-Engine (z.B. Docker), die die Container verwaltet und den Zugriff auf die Betriebssystem-Ressourcen koordiniert.
- **Gemeinsam genutzter Kernel**: Container teilen sich den Kernel des Host-Betriebssystems und benötigen daher kein eigenes Betriebssystem. Dies macht sie leichtgewichtiger.
- **Isolierung**: Container bieten Prozess- und Dateisystem-Isolierung, jedoch nicht die gleiche starke Isolierung wie VMs, da sie den gleichen Kernel verwenden.

### 2. Leistung

**Virtuelle Maschinen:**
- **Overhead**: VMs haben einen höheren Overhead, da sie ein vollständiges Betriebssystem ausführen müssen. Dies kann die Leistung beeinträchtigen, insbesondere bei I/O-intensiven Anwendungen.
- **Startzeit**: Das Booten einer VM dauert länger im Vergleich zu einem Container, da ein vollständiges Betriebssystem geladen werden muss.

**Container:**
- **Leichtgewichtig**: Container sind ressourceneffizienter, da sie den Kernel des Host-Systems nutzen und nicht das gesamte Betriebssystem virtualisieren müssen.
- **Startzeit**: Container starten schneller als VMs, oft in Sekundenbruchteilen, da sie nur die Anwendung und ihre Abhängigkeiten laden müssen.

### 3. Ressourcenverbrauch

**Virtuelle Maschinen:**
- **Speicher und CPU**: VMs benötigen mehr Speicher und CPU-Ressourcen, da jedes Gast-OS zusätzlichen Speicherplatz und CPU-Leistung beansprucht.
- **Ressourcenverwaltung**: Der Hypervisor muss die Ressourcen zwischen den VMs verwalten, was zusätzlichen Overhead verursacht.

**Container:**
- **Effizienz**: Container nutzen Ressourcen effizienter, da sie das Host-Betriebssystem teilen. Dies führt zu einem geringeren Speicher- und CPU-Bedarf.
- **Dichte**: Mehrere Container können auf dem gleichen Host ausgeführt werden, was eine höhere Dichte und bessere Ressourcennutzung ermöglicht.

### Zusammenfassung

**Virtuelle Maschinen (VMs):**
- Bieten starke Isolierung und Sicherheit durch vollständige Betriebssysteme.
- Haben höheren Overhead und längere Startzeiten.
- Sind ideal für Umgebungen, in denen vollständige Betriebssystem-Isolierung erforderlich ist.

**Container:**
- Sind leichtgewichtiger und effizienter, da sie den Kernel des Host-Systems nutzen.
- Haben geringeren Overhead und schnellere Startzeiten.
- Sind ideal für Microservices-Architekturen und Entwicklungsumgebungen, in denen Effizienz und Skalierbarkeit wichtig sind.

**Fazit:** Container sind in vielen modernen Anwendungsfällen, insbesondere in der Cloud-nativen Entwicklung und bei Microservices, eine bevorzugte Wahl aufgrund ihrer Effizienz und Flexibilität. Virtuelle Maschinen bleiben jedoch relevant für Szenarien, die eine starke Isolierung und Kompatibilität mit verschiedenen Betriebssystemen erfordern.

# Docker Tutorial #2 - Wie Docker arbeitet
Dieses Kapitel beschreibt die Funktionsweise von Docker. Wir erklären die Docker-Architektur, einschließlich Docker Daemon, Docker Client, Images und Container. Ein Überblick über die wichtigsten Docker-Komponenten und deren Zusammenspiel wird gegeben.

# Docker Tutorial #3 - Docker unter Linux installieren
Eine Schritt-für-Schritt-Anleitung zur Installation von Docker auf einem Linux-System. Wir behandeln die Installation über das offizielle Docker-Repository, das Hinzufügen des Docker GPG-Schlüssels und die Konfiguration des Docker-Daemons.

# Docker Tutorial #4 - Docker unter Windows installieren
Anleitung zur Installation von Docker Desktop auf Windows. Wir erklären die Systemanforderungen, die Installation von WSL 2 und die Konfiguration von Docker für die Verwendung unter Windows.

# Docker Tutorial #5 - Docker unter Mac installieren
In diesem Kapitel zeigen wir, wie Docker Desktop auf einem Mac installiert wird. Wir decken die erforderlichen Systemanforderungen ab und führen durch die Installation und Konfiguration.

# Nested VMs sind meistens eine schlechte Idee
Eine Diskussion darüber, warum verschachtelte virtuelle Maschinen oft ineffizient und problematisch sind. Wir erläutern die technischen Herausforderungen und warum Container eine bessere Lösung darstellen.

# Docker Tutorial #6 - Docker Compose unter Linux installieren
Anleitung zur Installation von Docker Compose auf einem Linux-System. Wir erklären die Verwendung von `curl`, um die neueste Version herunterzuladen und das Setup abzuschließen.

# Docker Tutorial #7 - Die Installation überprüfen
Schritte zur Überprüfung der Docker-Installation. Wir zeigen, wie man sicherstellt, dass der Docker-Daemon läuft und wie man einen einfachen Testcontainer startet, um die Funktionalität zu bestätigen.

# Docker Tutorial #8 - Eine Busybox starten
In diesem Kapitel starten wir einen Busybox-Container und führen einfache Befehle darin aus. Busybox ist ein leichtgewichtiges Image, das für Tests und Debugging nützlich ist.

# Docker Tutorial #9 - Befehle im inneren des Containers ausführen
Wir zeigen, wie man Befehle innerhalb eines laufenden Containers ausführt. Dabei wird der Unterschied zwischen `docker exec` und `docker attach` erklärt.

# Docker Tutorial #10 - WebApps und Port Mapping
Eine Anleitung zur Bereitstellung von Webanwendungen in Docker-Containern und zum Mappen von Ports vom Host auf den Container. Wir demonstrieren dies anhand eines einfachen Webservers.

# Docker Tutorial #11 - Der Detached Modus
Erklärung des Detached Modus in Docker. Wir zeigen, wie man Container im Hintergrund startet und wie man deren Logs und Status abruft.

# Docker Tutorial #12 - Eine Shell im Detached Mode erlangen
Schritte, um eine interaktive Shell in einem im Detached Mode laufenden Container zu erhalten. Wir verwenden `docker exec` für den Zugriff.

# Docker Tutorial #13 - Dateien an Container übergeben
In diesem Kapitel wird beschrieben, wie man Dateien zwischen dem Host und einem Docker-Container kopiert. Wir nutzen `docker cp` für diesen Zweck.

# Docker Tutorial #14 - Container stoppen, Löschen von Images und Containern
Anleitung zum Stoppen von Containern sowie zum Löschen von Docker-Images und -Containern. Wir erklären die entsprechenden Befehle und deren Optionen.

# Docker Tutorial #15 - Container automatisch starten lassen
Wir zeigen, wie man Docker so konfiguriert, dass Container automatisch beim Systemstart gestartet werden. Dazu verwenden wir Docker-Compose und systemd-Units.

# Docker Tutorial #16 - Statistiken der laufenden Container
Erklärung, wie man Statistiken zu Ressourcenverbrauch und Performance der laufenden Container abruft. Wir nutzen `docker stats` und erläutern die Ausgabe.

# Docker Tutorial #17 - Die Ressourcen eines Containers limitieren
In diesem Kapitel wird beschrieben, wie man die Ressourcen eines Containers (CPU, RAM) begrenzt. Wir verwenden Docker-Compose und die entsprechenden Docker-Befehle zur Ressourcensteuerung.

# Docker Tutorial #18 - Logs ansehen
Anleitung zum Abrufen und Analysieren von Logs aus Docker-Containern. Wir erklären die Verwendung von `docker logs` und die Konfiguration von Log-Driver.

# Docker Tutorial #19 - In eine Datei loggen
Schritte, um Docker-Logs in Dateien zu speichern. Wir konfigurieren den Docker-Daemon für das File-Logging und zeigen die notwendigen Einstellungen.

# Docker Tutorial #20 - Dockerfiles
Einführung in Dockerfiles, die Blaupausen für Docker-Images. Wir erklären die Struktur und die wichtigsten Anweisungen wie `FROM`, `RUN`, `COPY` und `CMD`.

# Docker Tutorial #21 - Dockerfiles builden und starten
Anleitung zum Erstellen und Starten von Docker-Images aus Dockerfiles. Wir verwenden `docker build` und `docker run` und demonstrieren den gesamten Prozess.

# Docker Tutorial #22 - Images auf Docker Hub teilen
Wir zeigen, wie man eigene Docker-Images auf Docker Hub veröffentlicht. Dies beinhaltet das Erstellen eines Docker Hub Accounts, das Taggen von Images und das Pushen auf das Repository.

# Docker Tutorial #23 - Environment Variablen
Erklärung der Verwendung von Environment-Variablen in Docker-Containern. Wir zeigen, wie man sie in Dockerfiles und Docker-Compose-Dateien definiert und verwendet.

# Docker Tutorial #24 - Python Deployment mit Docker
Anleitung zur Bereitstellung einer Python-Anwendung mit Docker. Wir erstellen ein Dockerfile für eine einfache Python-App und starten den Container.

# Docker Tutorial #25 - Nodejs Deployment mit Docker
Schritte zur Bereitstellung einer Node.js-Anwendung mit Docker. Wir erstellen ein Dockerfile für eine Node.js-App und demonstrieren die Bereitstellung.

# Docker Tutorial #26 - Ein Email Server mit MailCow
In diesem Kapitel zeigen wir, wie man einen vollständigen E-Mail-Server mit MailCow und Docker installiert und konfiguriert.

# Docker Tutorial #27 - Wordpress mit Docker installieren
Anleitung zur Installation und Konfiguration von Wordpress mit Docker. Wir verwenden Docker-Compose, um eine Wordpress-Umgebung bereitzustellen.

# Docker Tutorial #28 - Eine eigene Cloud mit Nextcloud
Schritte zur Einrichtung einer privaten Cloud mit Nextcloud und Docker. Wir konfigurieren Docker-Compose für die Bereitstellung von Nextcloud.

# Docker Tutorial #29 - Mehr Optionen in Docker Compose Files
Erklärung fortgeschrittener Optionen in Docker Compose Files. Wir behandeln Netzwerke, Volumes, Abhängigkeiten und weitere Einstellungen.

# Docker Tutorial #30 - Swarms
Einführung in Docker Swarm, eine Orchestrierungs- und Clustering-Technologie für Docker. Wir erklären die Grundlagen und die wichtigsten Konzepte.

# Docker Tutorial #31 - Docker Machine auf Linux installieren
Anleitung zur Installation von Docker Machine auf einem Linux-System. Wir zeigen, wie man virtuelle Maschinen für Docker verwaltet.

# Docker Tutorial #32 - Lokale virtuelle Maschinen erstellen
Schritte zur Erstellung lokaler virtueller Maschinen mit Docker Machine. Wir verwenden VirtualBox als Treiber und demonstrieren den Prozess.

# Docker Tutorial #33 - Zusätzliche Informationen über die VMs
In diesem Kapitel wird gezeigt, wie man zusätzliche Informationen und Details über die von Docker Machine verwalteten virtuellen Maschinen abruft.

# Docker Tutorial #34 - Einen Swarm erstellen
Anleitung zur Erstellung eines Docker Swarms. Wir konfigurieren Manager- und Worker-Knoten und initialisieren das Swarm-Cluster.

# Docker Tutorial #35 - Eine App im Swarm hosten
Schritte zur Bereitstellung einer Anwendung in einem Docker Swarm. Wir verwenden Docker-Compose zur Definition der Anwendung und starten sie im Swarm.

# Docker Tutorial #36 - Den Stack beenden, den Swarm verlassen
In diesem Kapitel zeigen wir, wie man einen Stack beendet und einen Knoten aus dem Swarm entfernt. Wir verwenden die entsprechenden Docker-Befehle und erläutern deren Anwendung.

# Docker Tutorial #37 - Ein Image nur auf dem Manager starten
Anleitung zum Starten eines Docker-Images ausschließlich auf einem Manager-Knoten im Swarm. Wir konfigurieren die Platzierungsrichtlinien entsprechend.

# Docker Tutorial #38 - Einen einzelnen Service im Cluster veröffentlichen
Schritte zur Veröffentlichung eines einzelnen Services im Docker Swarm Cluster. Wir erklären die Verwendung von `docker service create` und die Konfiguration von Service-Parametern.

# Docker Tutorial #39 - Services update
Anleitung zum Aktualisieren von Docker-Services im Swarm. Wir zeigen, wie man Rolling Updates durchführt und Ausfallzeiten minimiert.

# Docker Tutorial #40 - Letzte Worte
Ein abschließendes Kapitel mit wichtigen Tipps und Best Practices für die Arbeit mit Docker. Wir fassen die wichtigsten Punkte zusammen und geben Empfehlungen für weiterführende Ressourcen.

# Docker Tutorial Bonus - Joomla mit Docker aufsetzen
Eine Bonus-Anleitung zur Installation und Konfiguration von Joomla mit Docker. Wir nutzen Docker-Compose, um eine Joomla-Umgebung bereitzustellen.

# Docker Tutorial Bonus - Docker Compose Dateiformat Version
Erklärung der verschiedenen Versionen des Docker Compose Dateiformats. Wir zeigen die Unterschiede und neue Funktionen der aktuellen Versionen.
