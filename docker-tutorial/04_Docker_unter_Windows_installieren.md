### Docker Tutorial #4 - Docker unter Windows installieren

In diesem Tutorial zeigen wir Ihnen, wie Sie Docker Desktop auf einem Windows-System installieren. Dies umfasst die Systemanforderungen, die Installation des Windows-Subsystems für Linux (WSL 2) und die Konfiguration von Docker für den Einsatz unter Windows.

#### Systemanforderungen

Bevor Sie mit der Installation von Docker Desktop beginnen, stellen Sie sicher, dass Ihr System die folgenden Anforderungen erfüllt:

- **Windows-Version**: Windows 10 64-bit: Pro, Enterprise oder Education (ab Version 1903, Build 18362 oder höher)
- **Hardware**: 
  - 4 GB RAM oder mehr
  - Virtualisierungsunterstützung im BIOS aktiviert

#### Schritt 1: WSL 2 installieren

WSL 2 ist eine Voraussetzung für Docker Desktop auf Windows. Gehen Sie wie folgt vor, um WSL 2 zu installieren:

1. **WSL aktivieren**:
   Öffnen Sie PowerShell als Administrator und führen Sie den folgenden Befehl aus:

   ```powershell
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   ```

2. **Virtual Machine Platform aktivieren**:
   Führen Sie ebenfalls in PowerShell als Administrator den folgenden Befehl aus:

   ```powershell
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   ```

3. **Neustart des Systems**:
   Starten Sie Ihren Computer neu, um die Änderungen zu übernehmen.

4. **WSL 2 als Standardversion festlegen**:
   Nach dem Neustart öffnen Sie erneut PowerShell und setzen WSL 2 als Standardversion:

   ```powershell
   wsl --set-default-version 2
   ```

5. **Linux-Distribution installieren**:
   Öffnen Sie den Microsoft Store und installieren Sie eine Linux-Distribution Ihrer Wahl (z.B. Ubuntu).

#### Schritt 2: Docker Desktop installieren

1. **Docker Desktop herunterladen**:
   Besuchen Sie die [Docker Desktop-Website](https://www.docker.com/products/docker-desktop) und laden Sie die neueste Version von Docker Desktop für Windows herunter.

2. **Installationsprogramm ausführen**:
   Führen Sie das heruntergeladene Installationsprogramm aus und folgen Sie den Anweisungen des Installationsassistenten.

3. **WSL 2 Backend aktivieren**:
   Während der Installation werden Sie aufgefordert, WSL 2 als Backend zu aktivieren. Stellen Sie sicher, dass diese Option ausgewählt ist.

4. **Installation abschließen**:
   Nach Abschluss der Installation starten Sie Docker Desktop. Bei der ersten Ausführung werden Sie möglicherweise aufgefordert, sich anzumelden oder ein Docker-Konto zu erstellen.

#### Schritt 3: Docker konfigurieren

1. **Docker-Einstellungen öffnen**:
   Klicken Sie auf das Docker-Symbol in der Taskleiste und wählen Sie „Einstellungen“ aus.

2. **WSL-Integration aktivieren**:
   Navigieren Sie zu „Resources“ > „WSL Integration“ und aktivieren Sie die Integration für die installierte Linux-Distribution (z.B. Ubuntu).

3. **Docker testen**:
   Öffnen Sie eine PowerShell oder ein Linux-Terminal und führen Sie den folgenden Befehl aus, um zu überprüfen, ob Docker ordnungsgemäß installiert ist:

   ```bash
   docker run hello-world
   ```

Wenn Sie die Nachricht „Hello from Docker!“ sehen, war die Installation erfolgreich.

Herzlichen Glückwunsch! Sie haben Docker Desktop erfolgreich auf Ihrem Windows-System installiert und konfiguriert. Sie können nun Docker-Container erstellen und verwalten.