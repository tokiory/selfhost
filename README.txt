# Selfhost
Repository with configurations for running services on my own server.

=== === ===

## Devices
Currently the following devices are running on my network:
- Raspberry Pi 5 (8GB RAM)

My Raspberry Pi 5 is the main device hosting all the services. It is a powerful and energy-efficient single-board computer that allows me to run multiple services simultaneously without any performance issues.

Raspberry Pi hostname is **tokiopi**, so all services inside local network are accessible via **tokiopi.local**.
For example, if I have a service running on port 8080, I can access it by going to http://tokiopi.local:8080 in my web browser.

Other devices, that can access the services running on Raspberry Pi 5, include:
- Macbook Pro (M3 Pro, 18GB RAM)
- iPhone 16 Pro
- My wife's iPhone 17 Pro
- My wife's Macbook Air (M1, 8GB RAM)
- Our common iPad (M4)
- Our common Mac Mini (M1, 16GB RAM)

All these devices are connected to the same local network via Keenetic Router, also all these devices has static IP addresses, so they can access the services running on Raspberry Pi 5 without any issues bidirectionally.

**Future Plans**:
In the near future I'll buy an SSD for Raspberry Pi 5 and Zigbee dongle, so I can run Home Assistant and Zigbee2MQTT to control smart home devices.

=== === ===

## Services
- [Uptime Kuma](https://uptime.kuma.pet/): For monitoring the availability of services and their uptime;
- [Pihole](https://pi-hole.net/): For blocking ads and trackers at the network level;
- [Gitea](https://gitea.io/en-us/): For hosting my own Git repositories without relying on third-party services like GitHub or GitLab;
- [Traefik](https://traefik.io/): Reverse proxy for routing all web services through one entrypoint.

### Reverse Proxy Setup
Each web service is routed by Traefik using host-based rules.

1. Create Network:
- `docker network create traefik`

2. Change `.env` in the root of the repo:
- `cp .env{.example,}`
- `nvim .env`

There should be two variables:
- `HOST_NAME` - $HOST or $HOSTNAME variable from system
- `HOST_IP` - Host machine local IP address

3. Start core docker-compose that includes all services:
- `docker compose up -d`

### Troubleshooting

1. Bad gateway errors from subdomains:
- Check traefik network

2. Can not resolve domains:
- Check if your browser doesn't use any proxy
- Check domains inside labels of each `docker-compose.yml`

**Also note**: by default traefik will try to use default subdomains created by container name: `{{ CONTAINER_NAME }}.${ HOST_NAME }.local`
