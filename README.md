# Balena Home Assistant + AdGuard Home
Home Assistant and AdGuard Home in one device

balenaCloud is a free service to remotely manage and update your IoT devices through an online dashboard interface, as well as providing remote access to the AdGuard Home and Home Assistant web interface without any additional configuation.

This project is a [balenaCloud](https://www.balena.io/cloud) stack with the following services:
- [AdGuard Home](https://adguard.com/en/adguard-home/overview.html) is a network-wide software for blocking ads & tracking.
- [Home Assistant](https://www.home-assistant.io/) is a popular open source home automation system that is often run from low-cost devices like a Raspberry Pi. 

## Hardware required
Here’s the list of items required for a basic setup:

* Raspberry Pi 3B or greater (A B+ or 4B works great, and less powerful Pis can be used albeit with lower performance)
* 32GB (or larger) Micro-SD Card (we recommend Sandisk Extreme Pro SD cards)
* Power supply and cable

## Software required
This repository contains all of the software and configuration you’ll need to get started. We’re going to deploy this project on balenaCloud using a free account to push the project and all the software to your Raspberry Pi as well as to provide remote access. Therefore, you’ll need:

* A tool to flash your SD card, such as balenaEtcher
* A free balenaCloud account
* A clone or download of our project from GitHub

## Software setup

Running this project is as simple as deploying it to a balenaCloud application, then downloading the OS image from the dashboard and flashing your SD card.

[![](https://balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy)

We recommend this button as the de-facto method for deploying new apps on balenaCloud, but as an alternative, you can set this project up with the repo and balenaCLI if you choose. Get the code from this repo, and set up [balenaCLI](https://github.com/balena-io/balena-cli) on your computer to push the code to balenaCloud and your devices. [Read more](https://www.balena.io/docs/learn/deploy/deployment/).

## Configuring Home Assistant
A text editor called Hass-Configurator is available locally on port 3218. Using this editor, you can make changes to the Home Assistant configuration file /hass-config/configuration.yaml which is the default folder for Hass-Configurator.

After configuration, you may also use [AdGuard Home integration in Home Assistant.](https://www.home-assistant.io/integrations/adguard/)

## Configuring HASS Configurator
Environment varibles can be used to configure the configurator. For example, to add basic HTTP authentication, the `HC_USERNAME` and `HC_PASSWORD` variables can be specified. The password in plain text or via SHA256 by prepending the hash with `{sha256}`. For more information on configurator variables visit: https://github.com/danielperna84/hass-configurator/wiki/Configuration

Note that to specify any of these configuration variables as an environment variable they should be prepended with `HC_`.

## Configuring AdGuard Home

### Initial setup

<https://github.com/AdguardTeam/AdGuardHome/wiki/Getting-Started>

1. connect to `http://YOUR-DEVICE-IP:8000/install.html` in your browser
2. select the interface you want to use and any port that's not in use for the Admin Web Interface listen interface. Do not use ports 80 or 8080 as it'll be used by HomeAssistant. Any port above 1024 should be safe. Make sure to take note of the location as you'll use it to connect to the AdGuard Home Interface.
3. select either `eth0` or `wlan0` and port `53` for the DNS server listen interface depending on your use case.
4. provide an admin username and password

### Encryption setup

<https://github.com/AdguardTeam/AdGuardHome/wiki/Encryption>

Check out the `letsencrypt` branch on the following repo for instructions on using
certbot to automatically generate and renew SSL certificates.

<https://github.com/klutchell/balena-adguard/tree/letsencrypt>

## Acknowledgments

Original software is by AdGuard: <https://adguard.com/en/adguard-home/overview.html>

This repo combines two other projects on GitHub:
* [AdGuard Home on balena from klutchell](https://github.com/klutchell/balena-adguard)
* [Home Assistant on balena from balenalabs](https://github.com/balenalabs-incubator/balena-homeassistant)
