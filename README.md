# Home Lab Media Server Setup with Jellyfin and Docker Compose

This project provides a simple Docker Compose configuration to run a Jellyfin media server on your local machine or home lab environment.

## Overview

- Runs Jellyfin media server in a Docker container using an official image.
- Maps ports for easy access to the Jellyfin web UI (`http://localhost:8096`).
- Uses named Docker volumes to persist configuration and cache data.
- Bind mounts local media folder(s) to expose media files read-only to the server.
- Configured to restart automatically unless explicitly stopped.

## Docker Compose File Explanation

- `image: jellyfin/jellyfin`: Official Jellyfin media server image.
- `ports: 8096:8096`: Access the server UI via this port.
- `volumes:`  
  - `jellyfin-config:/config`: Stores Jellyfin settings.
  - `jellyfin-cache:/cache`: Stores cached metadata.
  - `C:/Users/Admin/movies:/media:ro`: Your media folder is mounted for Jellyfin to access.
- `restart: unless-stopped`: Container will restart automatically after crashes or reboots.

## How to Use

1. Install Docker and Docker Compose on your system.
2. Clone this repository.
3. Place your media files in the specified bind mount folder or adjust the path in `docker-compose.yaml`.
4. Run the server with:

    ```
    docker compose up -d
    ```

5. Open your browser at [http://localhost:8096](http://localhost:8096) to start using Jellyfin.

## Benefits

- Easy deployment and management of a personal media server.
- Uses Docker containers for isolation and portability.
- Persistent data storage with Docker volumes.
- Flexible media organization using bind mounts.

## Future Improvements --> working on it....

- Add SSL support with a reverse proxy (e.g., Nginx or Traefik).
- Automate backups of config and media.
- Add monitoring and alerting for server health.

---

*Created as a part of my home lab projects — sharing knowledge and practical containerized media management.*

