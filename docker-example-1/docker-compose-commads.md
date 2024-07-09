# docker-compose Datei  

## Container im Verbund starten
`docker-compose up -d`

## Container auflisten
`docker ps` oder `docker-compose ps`

## Container beenden
`docker-compose kill` oder `docker-compose stop` 

## Container & Co. aufräumen
docker netzwerke auslesen / liste: `docker network ls`
Container & Co. aufräumen ( alles wird entfernt auch netzwerke) --> `docker-compose down`
Container & Co. aufräumen (entfernt auch noch die volumes) --> `docker-compose down --volumes`

## sytsem aufräumen/ alle gespropten container wedren entfert mit volumes / es wird alles gelöscht was man nichtmehr braucht
`docker system prune --all --volumes`
mit `--all` wird sichergestellt das alle container gelöscht werden
mit `--volumes` wird sichergestellt das alle vituellen dateisysteme gelöscht werden

## Umgebungsvariablen eines containers_:
```
environment:
    - PORT
env_file:
    - .env
```
## Profiles - Organized services in profile grouping
start --> ` docker-compose --profile api up -d`
```
    profiles:
      - api
```
Besipiele: Unterschiedliche Datenbanken üunterstützen - je nach dem welches profil man auswählt wird eine andere datenbank gestartet

## Netzwerk konfiguration
nikla@MSI MINGW64 /c/0_projects/docker-example (docker-compose-example)
$ docker-compose up -d
time="2024-05-07T11:45:45+02:00" level=warning msg="C:\\0_projects\\docker-example\\docker-compose.yml: `version` is obsolete"
[+] Running 3/3
✔ Network docker-example_test     Created    --> anstatt default steht jetzt test                                                                                                                                                                                                                                                                 0.0s
✔ Container docker-example-api-1  Started                                                                                                                                                                                                                                                                     0.1s
✔ Container docker-example-ui-1   Started


## Beispiel Frontend & Backend
1. Dockerfile in api und ui ordner erstelle.
2. docker compose yml datei erstellen:
```
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
3. mehrere container starten 
```
   docker compose up
```
mehrere container im starten 
```
   docker compose up -d
```
4. Ausgabe:
```
nikla@MSI MINGW64 /c/0_projects/docker-example (docker-compose-example)
$ docker-compose up -d
time="2024-05-07T09:05:39+02:00" level=warning msg="C:\\0_projects\\docker-example\\docker-compose.yml: `version` is obsolete"
[+] Building 0.0s (0/0)  docker:default
[+] Building 28.0s (10/11)                                                                                                                                                                                                                                                                           docker:default
[+] Building 36.1s (18/18) FINISHED                                                                                                                                                                                                                                                                  docker:default
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
 => => transferring context: 2B                                                                                                                                                                                                                                                                                0.0s 
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

nikla@MSI MINGW64 /c/0_projects/docker-example (docker-compose-example)
$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS             PORTS                    NAMES
9ccfb8f1b02e   docker-example-ui    "/docker-entrypoint.…"   31 seconds ago   Up 31 seconds      0.0.0.0:4000->80/tcp     docker-example-ui-1
229f8d6e87d2   docker-example-api   "docker-entrypoint.s…"   32 seconds ago   Up 31 seconds      0.0.0.0:3000->3000/tcp   docker-example-api-1
d9851be6c16f   postgres:10.5        "docker-entrypoint.s…"   18 hours ago     Up About an hour   0.0.0.0:5432->5432/tcp   database-postgres-1

nikla@MSI MINGW64 /c/0_projects/docker-example (docker-compose-example)
$

```
# Beispiel Frontend & Backend - ohne docker compose zum laufen bringen
## Backend -  node js - api
1. erstelle api Ordner `cd api/`
2. erstelle package.json in api ordner `npm init`
```
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
3. dependecies erstelle: `npm install cors express flaschenpost`
```
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
4. erstelle app.js
```
'use strict';

const cors = require('cors');
const express = require('express');
const { flaschenpost} = require('flaschenpost');
const http = require("http");

const logger = flaschenpost.getLogger();
const api = express();

// CORS aktivieren
api.use(cors());
api.get('/', (req, res) => {
res.json({
now: Date.now()
});
});

const server = http.createServer(api);
const port = 3_000;

server.listen(port, () => {
logger.info('Server started. ', port)
});
```
5. serve starten:
```
nikla@MSI MINGW64 /c/0_projects/docker-example/api (docker-compose-example)
$ node app.js
Server started.  (info)
MSI::api@1.0.0 (C:\0_projects\docker-example\api\app.js)
07:41:32.015@2024-05-07 7732#0
3000
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

```
6. Dockerfile erstellen
```
FROM node:18.15.0-alpine

USER node
WORKDIR /home/node

COPY --chown=node:node ./package.json ./package.json
COPY --chown=node:node ./package-lock.json ./package-lock.json

RUN npm install --production

COPY --chown=node:node . .

CMD ["node", "app.js"]

```

7. `.dockerignore` datei erstellen
```
.git
node_modules

```
8. api Image bauen
```
docker build -t api .
```
9. test ob das image da ist mit `docker images`

10. container erstellen 
```
docker run -d --init -p 3000:3000 --name api api
```
11.  test oib es läuft:
```
docker ps
```
## Frontend - index.html 
1. ui ordner erstellen
```
mkdir ui
```
2index.html erstellen im ui ordner
```
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
        }, 1_000);
    </script>

</body>
</html>

```
3. Dockerfile erstellen:
```
FROM nginx:1.26.0-alpine
COPY index.html /usr/share/nginx/html

```
4. image ui bauen
```
docker build -t ui .
```
5. prüfe ob image da ist: `` docker images``
6. container bauen: in ui directory ausführen
a. eigenes image --> hier funktioniert de weiterleitung von der index.html 
```
docker run -d -p 4000:80 -v $(pwd):/usr/share/nginx/html:ro --name ui ui
```
b. über nginx image
``` 
docker run -d -p 4000:80 -v $(pwd):/usr/share/nginx/html --name ui nginx:1.26.0-alpine

```