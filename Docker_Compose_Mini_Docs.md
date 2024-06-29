# Docker-Compose Datei Anleitung

## Container im Verbund Starten
Um alle definierten Container im Hintergrund zu starten, verwenden Sie den folgenden Befehl:
```sh
docker-compose up -d
```

## Container Auflisten
Um eine Liste aller laufenden Container zu sehen, können Sie einen der folgenden Befehle verwenden:
```sh
docker ps
```
oder
```sh
docker-compose ps
```

## Container Beenden
Zum Stoppen oder Beenden von Containern, verwenden Sie:
```sh
docker-compose stop
```
oder
```sh
docker-compose kill
```

## Container & Co. Aufräumen
Um Docker-Netzwerke auszulesen, verwenden Sie:
```sh
docker network ls
```

Um alle Container, Netzwerke und zugehörige Ressourcen zu entfernen, verwenden Sie:
```sh
docker-compose down
```

Um auch die Volumes zu entfernen, verwenden Sie:
```sh
docker-compose down --volumes
```

## System Aufräumen
Um das gesamte System aufzuräumen und alle gestoppten Container sowie Volumes zu entfernen, verwenden Sie:
```sh
docker system prune --all --volumes
```
Mit `--all` wird sichergestellt, dass alle Container gelöscht werden. Mit `--volumes` wird sichergestellt, dass alle virtuellen Dateisysteme gelöscht werden.

## Umgebungsvariablen eines Containers
Um Umgebungsvariablen in einem Container zu setzen, können Sie das folgende Format in Ihrer `docker-compose.yml` Datei verwenden:
```yaml
environment:
    - PORT
env_file:
    - .env
```

## Profiles - Organisierte Dienste in Profil-Gruppierungen
Zum Starten eines bestimmten Profils, verwenden Sie:
```sh
docker-compose --profile api up -d
```
In der `docker-compose.yml` Datei können Sie Profile definieren:
```yaml
profiles:
    - api
```
Beispiel: Unterschiedliche Datenbanken unterstützen - je nach dem, welches Profil ausgewählt wird, wird eine andere Datenbank gestartet.

## Netzwerk Konfiguration
Wenn Sie Docker-Compose verwenden, um Container zu starten, können Sie Netzwerke konfigurieren. Beispiel:
```sh
docker-compose up -d
```
Eine typische Ausgabe könnte wie folgt aussehen:
```sh
time="2024-05-07T11:45:45+02:00" level=warning msg="C:\\0_projects\\docker-example\\docker-compose.yml: `version` is obsolete"
[+] Running 3/3
✔ Network docker-example_test     Created
✔ Container docker-example-api-1  Started
✔ Container docker-example-ui-1   Started
```

## Beispiel Frontend & Backend
### Schritt 1: Dockerfile in api und ui Ordner erstellen
### Schritt 2: `docker-compose.yml` Datei erstellen
```yaml
version: "0.1.1"

services:
    api:
        build: ./api
        ports:
            - 3000:3000
    ui:
        build: ./ui
        ports:
            - 4000:80
        volumes:
            - ./ui:/usr/share/nginx/html:ro
        depends_on:
            - api
```
### Schritt 3: Mehrere Container Starten
```sh
docker-compose up
```
Um die Container im Hintergrund zu starten:
```sh
docker-compose up -d
```

### Schritt 4: Beispielausgabe
```sh
time="2024-05-07T09:05:39+02:00" level=warning msg="C:\\0_projects\\docker-example\\docker-compose.yml: `version` is obsolete"
[+] Building 0.0s (0/0)  docker:default
[+] Building 28.0s (10/11)
[+] Building 36.1s (18/18) FINISHED
 => [api internal] load build definition from Dockerfile                                                                                                                                                                                                                                                       0.0s 
 => => transferring dockerfile: 304B                                                                                                                                                                                                                                                                           0.0s 
 => [api internal] load metadata for docker.io/library/node:18.15.0-alpine                                                                                                                                                                                                                                     1.5s
 => [api internal] load .dockerignore                                                                                                                                                                                                                                                                          0.0s 
 => => transferring context: 60B                                                                                                                                                                                                                                                                               0.0s 
 => [api 1/6] FROM docker.io/library/node:18.15.0-alpine@sha256:47d97b93629d9461d64197773966cc49081cf4463b1b07de5a38b6bd5acfbe9d                                                                                                                                                                              13.0s 
 => => resolve docker.io/library/node:18.15.0-alpine@sha256:47d97b93629d9461d64197773966cc49081cf4463b1b07de5a38b6bd5acfbe9d                                                                                                                                                                                   0.0s 
 => => sha256:51fa4270e0ccb40f31d39a195bac1ff5d1070909c60d8341690748af6abee321 47.54MB / 47.54MB                                                                                                                                                                                                               6.4s 
 => => sha256:a89e758f145e81ebe13f42f7831a348f212dcb3c17bc269201752bb76a9e52cf 2.35MB / 2.35MB                                                                                                                                                                                                                 2.0s 
 => => sha256:47d97b93629d9461d64197773966cc49081cf4463b1b07de5a38b6bd5acfbe9d 1.43kB / 1.43kB                                                                                                                                                                                                                 0.0s 
 => => sha256:a3f2350bd3eb48525f801b57934300c11aa3610086b708854ab1c1045c018519 1.16kB / 1.16kB                                                                                                                                                                                                                 0.0s 
 => => sha256:305c985a481fc143f40c3a5c1cb398756057851f3ab748e381c76fd1ce5b0177 6.48kB / 6.48kB                                                                                                                                                                                                                 0.0s 
 => => sha256:f56be85fc22e46face30e2c3de3f7fe7c15f8fd7c4e5add29d7f64b87abdaa09 3.37MB / 3.37MB                                                                                                                                                                                                                 2.0s 
 => => sha256:d3f921cbf16e91105a848c0cf6c365c0d7530152d264ce4bdd914a0a3ee00f82 453B / 453B                                                                                                                                                                                                                     2.1s 
 => => extracting sha256:f56be85fc22e46face30e2c3de3f7fe7c15f8fd7c4e5add29d7f64b87abdaa09                                                                                                                                                                                                                      0.2s
 => => extracting sha256:51fa4270e0ccb40f31d39a195bac1ff5d1070909c60d8341690748af6abee321                                                                                                                                                                                                                      5.9s
 => => extracting sha256:a89e758f145e81ebe13f42f7831a348f212dcb3c17bc269201752bb76a9e52cf                                                                                                                                                                                                                      0.2s 
 => => extracting sha256:d3f921cbf16e91105a848c0cf6c365c0d7530152d264ce4bdd914a0a3ee00f82                                                                                                                                                                                                                      0.0s 
 => [api internal] load build context                                                                                                                                                                                                                                                                          0.0s 
 => => transferring context: 40.51kB                                                                                                                                                                                                                                                                           0.0s 
 => [api 2/6] WORKDIR /home/node                                                                                                                                                                                                                                                                               0.4s 
 => [api 3/6] COPY --chown=node:node ./package.json ./package.json                                                                                                                                                                                                                                             0.1s 
 => [api 4/6] COPY --chown=node:node ./package-lock.json ./package-lock.json                                                                                                                                                                                                                                   0.1s 
 => [api 5/6] RUN npm install --production                                                                                                                                                                                                                                                                    11.9s 
 => [api 6/6] COPY --chown=node:node . .                                                                                                                                                                                                                                                                       0.1s 
 => [api] exporting to image                                                                                                                                                                                                                                                                                   0.9s 
 => => exporting layers                                                                                                                                                                                                                                                                                        0.9s 
 => => writing image sha256:9508e24dd3138a9b2c2561ed87848521b4a29260824dc32de5fa2f9958ae4ca2                                                                                                                                                                                                                   0.0s 
 => => naming to docker.io/library/docker-example-api                                                                                                                                                                                                                                                          0.0s 
 => [ui internal] load build definition from Dockerfile                                                                                                                                                                                                                                                        0.0s 
 => => transferring dockerfile: 100B                                                                                                                                                                                                                                                                           0.0s 
 => [ui internal] load metadata for docker.io/library/nginx:1.26.0-alpine                                                                                                                                                                                                                                      2.1s 
 => [ui internal] load .dockerignore                                                                                                                                                                                                                                                                           0.0s 
 => => transferring context: 2B                                                                                                                                                                                                                                                                                

 0.0s 
 => [ui internal] load build context                                                                                                                                                                                                                                                                           0.0s 
 => => transferring context: 894B                                                                                                                                                                                                                                                                              0.0s 
 => [ui 1/2] FROM docker.io/library/nginx:1.26.0-alpine@sha256:ef587d1eb99e991291c582bfb74f27db27f7ca2c095d4ba06cc3f7c910a0c7b3                                                                                                                                                                                4.0s 
 => => resolve docker.io/library/nginx:1.26.0-alpine@sha256:ef587d1eb99e991291c582bfb74f27db27f7ca2c095d4ba06cc3f7c910a0c7b3                                                                                                                                                                                   0.0s 
 => => sha256:daaa4efb3bb69b5c32a99a6bf17a88b94d793dcef4155e25966b3fc939f2e8f7 2.50kB / 2.50kB                                                                                                                                                                                                                 0.0s 
 => => sha256:51c6306186bfa8d72a599f9a6681170f6fc49ae71e550ed91d5e5f29de5396dd 628B / 628B                                                                                                                                                                                                                     0.9s 
 => => sha256:4abcf20661432fb2d719aaf90656f55c287f8ca915dc1c92ec14ff61e67fbaf8 3.41MB / 3.41MB                                                                                                                                                                                                                 0.6s 
 => => sha256:3129a53fcac06e353923c712ac89f1f615351d6caebeff843f8541dc108e5f62 3.99MB / 3.99MB                                                                                                                                                                                                                 1.1s 
 => => sha256:ef587d1eb99e991291c582bfb74f27db27f7ca2c095d4ba06cc3f7c910a0c7b3 9.06kB / 9.06kB                                                                                                                                                                                                                 0.0s 
 => => sha256:aad9d2c57addc25b3941723ed63bfbf78ff0628f1179f639ed9ed647bfbbda78 10.79kB / 10.79kB                                                                                                                                                                                                               0.0s 
 => => extracting sha256:4abcf20661432fb2d719aaf90656f55c287f8ca915dc1c92ec14ff61e67fbaf8                                                                                                                                                                                                                      0.2s 
 => => sha256:097adf26662dbcb8353dbab98f92447c8fcc8dd10e6b3e7277ab15c4f07020db 954B / 954B                                                                                                                                                                                                                     0.9s 
 => => sha256:7101c757445269bb0ba0f116a908a9855835bd10f03033a6a25839de99bf6f49 1.21kB / 1.21kB                                                                                                                                                                                                                 1.1s 
 => => sha256:27b4ece6aebb1921391be4df28d47f78830882996352fe80d453ebd7c26e58f9 393B / 393B                                                                                                                                                                                                                     1.1s 
 => => extracting sha256:3129a53fcac06e353923c712ac89f1f615351d6caebeff843f8541dc108e5f62                                                                                                                                                                                                                      0.4s 
 => => sha256:b1a0e0d8fc1d10549523ad6e8c172c18bb45a23a86238dc3eca377a5336485b1 13.04MB / 13.04MB                                                                                                                                                                                                               2.7s 
 => => sha256:98679bd100072c2c5ab40d385bcfaf94fcb1e98d05121db1a5273bf5c52ac448 1.40kB / 1.40kB                                                                                                                                                                                                                 1.3s 
 => => extracting sha256:51c6306186bfa8d72a599f9a6681170f6fc49ae71e550ed91d5e5f29de5396dd                                                                                                                                                                                                                      0.0s 
 => => extracting sha256:097adf26662dbcb8353dbab98f92447c8fcc8dd10e6b3e7277ab15c4f07020db                                                                                                                                                                                                                      0.0s 
 => => extracting sha256:27b4ece6aebb1921391be4df28d47f78830882996352fe80d453ebd7c26e58f9                                                                                                                                                                                                                      0.0s 
 => => extracting sha256:7101c757445269bb0ba0f116a908a9855835bd10f03033a6a25839de99bf6f49                                                                                                                                                                                                                      0.0s 
 => => extracting sha256:98679bd100072c2c5ab40d385bcfaf94fcb1e98d05121db1a5273bf5c52ac448                                                                                                                                                                                                                      0.0s 
 => => extracting sha256:b1a0e0d8fc1d10549523ad6e8c172c18bb45a23a86238dc3eca377a5336485b1                                                                                                                                                                                                                      0.9s 
 => [ui 2/2] COPY index.html /usr/share/nginx/html                                                                                                                                                                                                                                                             1.3s 
 => [ui] exporting to image                                                                                                                                                                                                                                                                                    0.1s 
 => => exporting layers                                                                                                                                                                                                                                                                                        0.0s 
 => => writing image sha256:48f2f62a963d6a954965425d405c3e892a5ad9f53db885b170c426006dd316a7                                                                                                                                                                                                                   0.0s 
 => => naming to docker.io/library/docker-example-ui                                                                                                                                                                                                                                                           0.0s 
[+] Running 3/3
 ✔ Network docker-example_default  Created                                                                                                                                                                                                                                                                     0.1s 
 ✔ Container docker-example-api-1  Started                                                                                                                                                                                                                                                                     0.2s 
 ✔ Container docker-example-ui-1   Started                                                                                                                                                                                                                                                                     0.1s 
```

### Schritt 5: Verifizierung
Um zu überprüfen, ob die Container laufen:
```sh
docker ps
```
Die Ausgabe sollte ähnlich aussehen:
```sh
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS             PORTS                    NAMES
9ccfb8f1b02e   docker-example-ui    "/docker-entrypoint.…"   31 seconds ago   Up 31 seconds      0.0.0.0:4000->80/tcp     docker-example-ui-1
229f8d6e87d2   docker-example-api   "docker-entrypoint.s…"   32 seconds ago   Up 31 seconds      0.0.0.0:3000->3000/tcp   docker-example-api-1
d9851be6c16f   postgres:10.5        "docker-entrypoint.s…"   18 hours ago     Up About an hour   0.0.0.0:5432->5432/tcp   database-postgres-1
```

## Beispiel Frontend & Backend - Ohne Docker Compose
### Backend - Node.js API
1. **Erstellen Sie den API-Ordner:**
   ```sh
   cd api/
   ```

2. **Erstellen Sie `package.json` im API-Ordner:**
   ```sh
   npm init
   ```
   Inhalt von `package.json`:
   ```json
   {
     "name": "api",
     "version": "1.0.0",
     "description": "",
     "main": "index.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "author": "",
     "license": "ISC"
   }
   ```

3. **Installieren Sie Abhängigkeiten:**
   ```sh
   npm install cors express flaschenpost
   ```
   Inhalt von `package.json` nach der Installation:
   ```json
   {
     "name": "api",
     "version": "1.0.0",
     "description": "",
     "main": "index.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "author": "",
     "license": "ISC",
     "dependencies": {
       "cors": "^2.8.5",
       "express": "^4.19.2",
       "flaschenpost": "^5.1.1"
     }
   }
   ```

4. **Erstellen Sie `app.js`:**
   ```javascript
   'use strict';

   const cors = require('cors');
   const express = require('express');
   const { flaschenpost } = require('flaschenpost');
   const http = require("http");

   const logger = flaschenpost.getLogger();
   const api

 = express();

   // CORS aktivieren
   api.use(cors());
   api.get('/', (req, res) => {
     res.json({
       now: Date.now()
     });
   });

   const server = http.createServer(api);
   const port = 3000;

   server.listen(port, () => {
     logger.info('Server started.', port);
   });
   ```

5. **Starten Sie den Server:**
   ```sh
   node app.js
   ```

### Frontend - `index.html`
1. **Erstellen Sie den UI-Ordner:**
   ```sh
   mkdir ui
   ```

2. **Erstellen Sie `index.html` im UI-Ordner:**
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>My Website</title>
       <style>
           body {
               width: 100vw;
               height: 100vh;
               display: flex;
               align-items: center;
               justify-content: center;
           }

           #now {
               font-family: sans-serif;
               font-size: 2em;
           }
       </style>
   </head>
   <body>
       <div id="now"></div>

       <script>
           const $now = document.querySelector('#now');

           setInterval(async () => {
               const response = await fetch('http://localhost:3000');
               const { now } = await response.json();

               $now.innerHTML = new Date(now);
           }, 1000);
       </script>

   </body>
   </html>
   ```

3. **Erstellen Sie das Dockerfile für das Frontend:**
   ```Dockerfile
   FROM nginx:1.26.0-alpine
   COPY index.html /usr/share/nginx/html
   ```

4. **Erstellen Sie das Image für das Frontend:**
   ```sh
   docker build -t ui .
   ```

5. **Prüfen Sie, ob das Image vorhanden ist:**
   ```sh
   docker images
   ```

6. **Erstellen und starten Sie den Container:**
   ```sh
   docker run -d -p 4000:80 -v $(pwd):/usr/share/nginx/html:ro --name ui ui
   ```

Oder verwenden Sie das Nginx-Image:
   ```sh
   docker run -d -p 4000:80 -v $(pwd):/usr/share/nginx/html --name ui nginx:1.26.0-alpine
   ```

### Testen Sie die Anwendung
1. **Backend:**
   ```sh
   node app.js
   ```

2. **Frontend:**
   ```sh
   docker run -d -p 4000:80 -v $(pwd):/usr/share/nginx/html:ro --name ui ui
   ```

3. **Überprüfen Sie die laufenden Container:**
   ```sh
   docker ps
   ```

Jetzt sollten beide Container (API und UI) laufen, und Sie können das Frontend über `http://localhost:4000` erreichen, das Daten von der API (`http://localhost:3000`) abruft.