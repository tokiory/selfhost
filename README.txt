# Selfhost
Repository with configurations for running services on my own server.

=== === ===

## Devices
Currently the following devices are running on my network:
- Raspberry Pi 5 (8GB RAM)

My Raspberry Pi 5 is the main device hosting all the services. It is a powerful and energy-efficient single-board computer that allows me to run multiple services simultaneously without any performance issues.

Raspberry Pi hostname is tokiopi, so all services inside local network are accessible via **tokiopi.local**.
For example, if I have a service running on port 8080, I can access it by going to http://tokiopi.local:8080 in my web browser.

Other devices, that can access the services running on Raspberry Pi 5, include:
- Macbook Pro (M3 Pro, 18GB RAM)
- iPhone 16 Pro
- My wife's iPhone 17 Pro
- My wife's Macbook Air (M1, 8GB RAM)
- Our common iPad (M4)
- Our common Mac Mini (M1, 16GB RAM)

In the near future I'll buy an SSD for Raspberry Pi 5 and Zigbee dongle, so I can run Home Assistant and Zigbee2MQTT to control smart home devices.

=== === ===

## Services
- [Uptime Kuma](https://uptime.kuma.pet/): For monitoring the availability of services and their uptime;
- [Pihole](https://pi-hole.net/): For blocking ads and trackers at the network level;
