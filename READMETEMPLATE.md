![http://linuxserver.io](http://www.linuxserver.io/wp-content/uploads/2015/06/linuxserver_medium.png)

The [LinuxServer.io](https://www.linuxserver.io/) team brings you another quality container release featuring auto-update on startup, easy user mapping and community support. Be sure to checkout our [forums](https://forum.linuxserver.io/index.php) or for real-time support our [IRC](https://www.linuxserver.io/index.php/irc/) on freenode at `#linuxserver.io`.

# linuxserver/sickbeard

The ultimate PVR application that searches for and manages your TV shows
Automatically finds new and old episodes for you and it works with your current download client!. Includes updated python ssl for newer sites like PTP etc.[Sickbeard](http://sickbeard.com/)

## Usage

```
docker create --name=sickbeard -v /etc/localtime:/etc/localtime:ro -v <path to data>:/config -v <path to downloads>:/downloads -v <path to tv-shows>:/tv -e PGID=<gid> -e PUID=<uid>  -p 8081:8081 linuxserver/sickbeard
```

**Parameters**

* `-p 8081` - the port(s)
* `-v /etc/localtime` for timesync - *optional*
* `-v /config` - where sickbeard should store its config files etc.
* `-v /downloads` - your downloads folder
* `-v /tv` - your tv-shows folder
* `-e PGID` for GroupID - see below for explanation
* `-e PUID` for UserID - see below for explanation
* `-e TZ` for timezone information eg Europe/London, etc

It is based on phusion-baseimage with ssh removed, for shell access whilst the container is running do `docker exec -it sickbeard /bin/bash`.

### User / Group Identifiers

**TL;DR** - The `PGID` and `PUID` values set the user / group you'd like your container to 'run as' to the host OS. This can be a user you've created or even root (not recommended).

Part of what makes our containers work so well is by allowing you to specify your own `PUID` and `PGID`. This avoids nasty permissions errors with relation to data volumes (`-v` flags). When an application is installed on the host OS it is normally added to the common group called users, Docker apps due to the nature of the technology can't be added to this group. So we added this feature to let you easily choose when running your containers.

## Setting up the application 

Web interface is at :8081 , set paths for downloads, tv-shows to match docker mappings via the webui.


## Updates

* Upgrade to the latest version simply `docker restart sickbeard`.
* To monitor the logs of the container in realtime `docker logs -f sickbeard`.



## Versions

+ **03.11.2015:** Initial Release. 


