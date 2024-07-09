# docker commands

##  docker images
`docker pull image_name`
`docker pull image_name:version_nr`
Example: 
`docker pull ubuntu`
`docker pull ubuntu:22.04`

# Wie aktualiesiere ich ein docker images oder alle dokcer images?

## docker images liste
`docker images`

## docker container liste
`docker ps`
`docker ps -a`

## docker conrainer ausführen
`docker run` nimmt das ausgewählte image und macht daraus einen container.
Aus einen image kann es mehrere container (instancen geben)
`bash` bash prozess ausführen
`-it` bedeutet interaktiv starten - im terminal öffnet damit ich eingaben machen kann
`docker run -it image_name bash`
-d läuft im hintergrund
`docker run -d image_name bash`
container mit custom namen erstellen und starten:
`docker run -d --name webserve image:version`
Example
`docker run -it ubunu bash`
`docker run -it ubunu:22.04 bash`

## container / prozess  logs
`docker logs name_container`
`docker logs id_container`
logs live verfolgen:
`docker logs --follow name_container` = `docker logs -f name_container`

## docker container beenden
`docker stop container_name`
`docker stop container_id`

## docker container stecker ziehen
`docker kill container_name`
`docker kill container_id`

## docker container löschen / entfernen 
`docker rm container_name`
`docker rm container_id`

## docker images löschen / entfernen
`docker rmi container_name`
`docker rmi container_id`

## sytsem aufräumen/ alle gespropten container wedren entfert mit volumes / es wird alles gelöscht was man nichtmehr braucht 
`docker system prune --all --volumes`
 mit `--all` wird sichergestellt das alle container gelöscht werden
 mit `--volumes` wird sichergestellt das alle vituellen dateisysteme gelöscht werden

## ports weiterleiten / nginx

1. neuer container erstellen: `docker run -d --name webserve nginx` --> container mit custom namen erstellen und starten:
   `docker run -d --name webserve image:version`
2. 


