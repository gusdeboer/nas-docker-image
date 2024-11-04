# QNAP Servarr docker compose 

This is a docker compose file for setting up the Servarr landscape on a QNAP NAS.

## Prerequisites

- QNAP NAS
- Container Station installed
- Docker installed
- Portainer installed (optional)

## Services

- Prowlarr (Indexer and Tracker)
- Sonarr (TV Shows)
- Radarr (Movies)
- Bazarr (Subtitles)
- Overseerr (Requests)
- qBittorrent (Torrent client)
- nzbget (Usenet client)
- Plex (Media server)

## Installation

Go to the QNAP web interface and open Container Station. Click on the `+` icon in the top right corner and select 
`Create Application`. Select `Docker Compose` and paste the contents of the `docker-compose.yml` file into the editor. 
Click `Create` to start the services.

## Steps

### Prowlarr
1. Open Prowlarr in your browser by going to `http://<NAS_IP>:9696`.
2. Follow the setup wizard to configure Prowlarr.
3. Add indexers and trackers to Prowlarr.
4. Configure Sonarr, Radarr to use Prowlarr as the indexer using the API keys from both applications

### Sonarr

1. Open Sonarr in your browser by going to `http://<NAS_IP>:8989`.
2. Follow the setup wizard to configure Sonarr.
3. Add qBitTorrent or NZBGet as the download client.

### qBittorrent

1. Open qBittorrent in your browser by going to `http://<NAS_IP>:8181`.
2. Configure the download folder to `/share/downloads` and the watch folder to `/downloads/watch`.

## Tips

- While setting up the service make sure to use the docker container name in the host field instead of the IP address.
- You cannot edit the compose file after creating the application. You will have to delete the application and create a 
new one.
- You can get the PGID and PIUD using the following commands
    ```
    id -u <username>
    id -g <groupname>
    ```
- You can use the `docker exec -it <container_name> bash` command to get a shell inside the container.