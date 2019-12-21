# Pi-Hole Monitoring with Grafana #

## Overview ##
This package was built for the sole purpose of making the installation of grafana, telegraf, and influxdb to monitor a Pi-Hole instance as painless as possible. Typically, a user would need lots of setup to on each package in order to correctly monitor Pi-Hole. This package does as much as possible for you. No installing each package, no exposing ports on your machine, and no searching for hours on how to build and copy grafana dashboards. It's all already included here. Just follow the instructions below and enjoy!

## Example Dashboards ##
<img src="https://i.imgur.com/i2zoeb0.png" width=300/><img src="https://i.imgur.com/x4AssYP.png" width=300/>

## Prerequisites ##
- You need a working copy of Pi-Hole with its `pihole-FTL.db` file located at `/etc/pihole/` (i.e. this doesn't work out-of-the-box with Pi-Hole Docker containers or special installations). If your Pi-Hole instance is not located there, simply change [this line of code](https://github.com/Brandawg93/Pi-Hole-Monitoring/blob/master/docker-compose.yml#L16) to point to the folder that contains `pihole-FTL.db`.

## Known Issues ##
This project was developed on raspbian buster. As such, issues may arise when running this on anything else. See [this issue](https://github.com/Brandawg93/Pi-Hole-Monitoring/issues/3#issuecomment-568185900) for more details.

## Instructions ##
(If you have already installed docker-compose skip to step 7.)

1. Install Docker

  `curl -sSL https://get.docker.com | sh`

2. Add permission to Pi User to run Docker Commands

  `sudo usermod -aG docker pi`
  
3. Reboot!

4. Test Docker installation

  `docker run hello-world`
  
5. Install dependencies

  `sudo apt-get install libffi-dev libssl-dev`

  `sudo apt-get install -y python python-pip`

  `sudo apt-get remove python-configparser`

6. Install Docker Compose

  `sudo pip install docker-compose`
  
7. Clone this repo

  `git clone https://github.com/Brandawg93/Pi-Hole-Monitoring.git`
  
8. Change directory into cloned repo

  `cd Pi-Hole-Monitoring`

9. Start the stack

  `docker-compose up -d`

10. Go to http://host_ip:3000 (where host_ip is the ip of the machine running the stack)

11. Type `admin` for the username and `admin` for the password

12. Set your new password

13. Done!

## Updating ##
This is an ongoing project that may be updated frequently. If you would like the update your instance of Pi-Hole Monitoring, simply run the following commands:

`docker-compose down`

`git pull origin master`

`docker-compose up -d`
