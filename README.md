# App-Netbootxyz

## First Time Prerequisites

1. `rm ./Data/example/.gitkeep`
2. Run [Traefik](https://github.com/HackingServerHomelab/App-Traefik)

## Running the Containers

1. Update the following volumes in [docker-compose.yml](./Docker/docker-compose.yml)
    * `../Data/config:/config`
    * `../Data/assets:/assets`
2. Update the Traefik host labels in [docker-compose.yml](./Docker/docker-compose.yml)
    * ``"traefik.http.routers.netboot-pxe.rule=Host(`localhost`)"``
    * ``"traefik.http.routers.netboot-admin.rule=Host(`localhost`)"``
3. Run `docker-compose -f ./Docker/docker-compose.yml up -d`

## First Time Setup

1. Visit <https://your-ip>
2. Configure your systems to use Netboot. [Documentation is here.](https://netboot.xyz/booting/)
    Specifically, with a Unifi Security Gateway (with the controller):
	1. Networks -> LAN (or the network you want to boot from) -> ADVANCED DHCP OPTIONS
    2. Enable network boot: Checked
    3. Server: <your-ip>
    4. Filename: `netboot.xyz.kpxe`
