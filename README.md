# doomsday
Docker Container for [Doomsday Engine](http://wiki.dengine.net/w/Multiplayer_server) Server.

This container does the following things,

- Configures Ubuntu 16.06 to run Doomsday
- Downloads and installs a version of Doomsday
- Downloads Doom1 Shareware WAD

## Building

Build the container

```
docker built -t doomsday .
```

# Running
Run this container with the following options to run a Doom1 Shareware deathmatch inclued in this repository

```
docker run -it --rm -p 13209:13209 doomsday -game doom1-share -p /app/autoexec.cfg -iwad /app -port 13209 -stdout
```

Run this container by using a volume mount of the local directory containing a `autoexec.cfg` and WADS

```
docker run -it --rm -p 13209:13209 -v `pwd`:/app -game doom1-share -p /app/autoexec.cfg -iwad /app -port 13209 -stdout
```

Update the command line options to meet the game type, port etc. See the [Doomsday Multiplayer Server](http://wiki.dengine.net/w/Multiplayer_server) for additional options and configuration.
