# videonet

A collection of services for requesting, downloading, managing, and viewing tv shows and movies.

##### Install
```
git clone https://github.com/jasperalani/videonet
cd videonet

# windows
mkdir jellyfin jellyfin\cache jellyfin\config nginx\certs nginx\logs petio petio\logs plex plex\config plex\transcode prowlarr qbittorrent\downloads radarr radarr\config radarr\movies sonarr sonarr\config sonarr\tv

# mac/unix
mkdir -p jellyfin/cache jellyfin/config nginx/certs nginx/logs petio/logs plex/config plex/transcode prowlarr qbittorrent/downloads radarr/config radarr/movies sonarr/config sonarr/tv

docker compose up --build --remove-orphans
```

⚠️ HTTPS is not configured by default.

### Services
- mongodb
  - ⚠️ not included, you must run a mongodb server yourself
- sonarr
    - http://localhost:8989/
    - Manage tv show downloads
- radarr
    - http://localhost:7878/
    - Manage movie downloads
- prowlarr
    - http://localhost:9696/
    - Torrent indexer
- flaresolverr
    - http://localhost:8191/
    - Proxy server to bypass Cloudflare protection
- jellyfin
    - http://localhost:8096
    - Media server
- petio
    - http://localhost:7777
    - Request content for download
    - use `host.docker.internal:27017` for connecting to mongodb
- plex
    - http://localhost:32400
    - Supplies media metadata for petio
- qbittorrent
    - http://localhost:8081/
    - Torrent download client
    - Preconfigured files:
      - [`qBittorrent.conf`](qbittorrent/qBittorrent.conf)
      - [`categories.json`](qbittorrent/categories.json)
- nginx dashboard
  - http://localhost
  - Simple dashboard for checking service health
  - Preconfigured files:
    - [`nginx.conf`](nginx/nginx.conf)


### Diagram
![Services Diagram](videonet%20diagram.png "Services Diagram")

### Todo
- Add url for setup wizard for each service in this readme
- Fix bug qbittorrent link doesnt work on dashboard