# WebApps und Port Mapping | WebApps and Port Mapping

## Docker Pull Befehl | Docker Pull Command

### Verwendung von `docker pull nginx` | Using `docker pull nginx`

#### Deutsch:
Der Befehl `docker pull nginx` wird verwendet, um das Nginx-Image aus dem Docker Hub herunterzuladen. Nginx ist ein weit verbreiteter Webserver und Reverse-Proxy-Server. 

```bash
docker pull nginx
```

Nach der Eingabe dieses Befehls wird Docker das neueste Nginx-Image aus dem Docker-Repository herunterladen und auf Ihrem lokalen System speichern. Dies ermöglicht es Ihnen, das heruntergeladene Image später zu verwenden, um Container zu erstellen und auszuführen.

#### English:
The command `docker pull nginx` is used to download the Nginx image from Docker Hub. Nginx is a widely used web server and reverse proxy server.

```bash
docker pull nginx
```

After entering this command, Docker will download the latest Nginx image from the Docker repository and store it on your local system. This allows you to use the downloaded image later to create and run containers.

## Docker Run Befehl | Docker Run Command

### Verwendung von `docker run nginx` | Using `docker run nginx`

#### Deutsch:
Der Befehl `docker run nginx` wird verwendet, um einen neuen Container basierend auf dem heruntergeladenen Nginx-Image zu erstellen und auszuführen. 

```bash
docker run nginx
```

Nach der Eingabe dieses Befehls wird Docker einen neuen Container erstellen und den Nginx-Server innerhalb dieses Containers starten. Dies ist nützlich für die einfache Bereitstellung und das Testen von Nginx auf Ihrem lokalen System.

#### English:
The command `docker run nginx` is used to create and run a new container based on the downloaded Nginx image.

```bash
docker run nginx
```

After entering this command, Docker will create a new container and start the Nginx server within this container. This is useful for easily deploying and testing Nginx on your local system.

### Verwendung von `docker run -p 5000:80 nginx` | Using `docker run -p 5000:80 nginx`

#### Deutsch:
Der Befehl `docker run -p 5000:80 nginx` wird verwendet, um einen neuen Container zu erstellen und einen Port-Mapping zwischen dem Host und dem Container zu konfigurieren. 

```bash
docker run -p 5000:80 nginx
```

In diesem Fall wird der Port 5000 des Hosts auf den Port 80 des Containers gemappt. Dies bedeutet, dass Sie auf den Nginx-Server zugreifen können, indem Sie `http://localhost:5000` in Ihrem Webbrowser eingeben. Der Port 80 ist der Standardport für HTTP-Dienste innerhalb des Containers.

#### English:
The command `docker run -p 5000:80 nginx` is used to create a new container and configure port mapping between the host and the container.

```bash
docker run -p 5000:80 nginx
```

In this case, port 5000 of the host is mapped to port 80 of the container. This means you can access the Nginx server by entering `http://localhost:5000` in your web browser. Port 80 is the default port for HTTP services within the container.

## Port-Weiterleitung | Port Forwarding

### Verwendung von Port-Weiterleitung in Docker | Using Port Forwarding in Docker

#### Deutsch:
Die Port-Weiterleitung in Docker wird verwendet, um den Netzwerkverkehr von einem spezifischen Port des Hosts an einen spezifischen Port des Containers weiterzuleiten. Dies ermöglicht es Ihnen, auf Dienste im Container über den Host zuzugreifen.

#### Beispiel:
Angenommen, Sie möchten den Webserver in einem Docker-Container auf Port 80 ausführen, aber der Zugriff soll über Port 5000 des Hosts erfolgen. Der Befehl lautet:

```bash
docker run -p 5000:80 nginx
```

Dies leitet den gesamten HTTP-Verkehr vom Host-Port 5000 an den Container-Port 80 weiter, sodass Sie den Webserver über `http://localhost:5000` erreichen können.

#### English:
Port forwarding in Docker is used to forward network traffic from a specific port on the host to a specific port on the container. This allows you to access services running in the container through the host.

#### Example:
Suppose you want to run the web server in a Docker container on port 80 but access it through port 5000 on the host. The command is:

```bash
docker run -p 5000:80 nginx
```

This forwards all HTTP traffic from host port 5000 to container port 80, allowing you to reach the web server at `http://localhost:5000`.