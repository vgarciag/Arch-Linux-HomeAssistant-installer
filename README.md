# To install Home Assitant into Arch Linux and Raspberry Pi.

Steps to Install Home Assistant into Rapsberry Pi 4 with Arch Linux

## Prerequisites:

- RaspPi4 with archlinux: https://archlinuxarm.org 
- some SW:
	curl, bash, docker-ce, dbus, apparmor, jq, systemd, os-agent To-Do

## Installation

This repo is strongly linked to https://github.com/home-assistant/supervised-installer because some resources are downloaded from this
repository.

Copy the files [/etc](https://github.com/home-assistant/supervised-installer/tree/main/homeassistant-supervised/etc) and [/usr](https://github.com/home-assistant/supervised-installer/tree/main/homeassistant-supervised/usr) into respectives 
`/etc` and `/usr` directories in server with a valid permissions. 

it can be done by cloning the repository.

Execute: [`installer_hassio_supervised.sh`](installer_hassio_supervised.sh) which is based in https://github.com/home-assistant/supervised-installer/blob/main/homeassistant-supervised/DEBIAN/postinst

Note: the script has the next modifications:
	- commented `. /usr/share/debconf/confmodule` at line #6
	- commented the section in which the Network manager is enabled.
	- harcoded the env var `MACHINE` to `MACHINE="raspberrypi4-64"`

```bash
bash installer_hassio_supervised.sh 
```

## Throubleshoting

Once installed the H.A. the service has a cli service to don things when the web interface doesn't works:

It cat be called with `ha` command (ha is a script that really invokes a command inside docker instance) more info: [home-assistant/cli](https://github.com/home-assistant/cli)

usefull commands

- `ha core update`
- `ha su repair`
- `ha supervisor repair`
- `ha host reboot`

