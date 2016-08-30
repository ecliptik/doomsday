[![](https://images.microbadger.com/badges/image/ecliptik/doomsday.svg)](http://microbadger.com/images/ecliptik/doomsday "Get your own image badge on microbadger.com")

# doomsday
Docker Container for [Doomsday Engine](http://wiki.dengine.net/w/Multiplayer_server) Server.

Dockerfile builds the following,

- Ubuntu 16.04 and packages to run Doomsday 2.0
- Downloads and installs Doomsday 2.0
- Downloads Doom1 Shareware WAD
- Add basic deathmatch `autoexec.cfg`

## Building

Build the container

```
docker build -t doomsday .
```

# Running
Run this container with the following options to run a Doom1 Shareware deathmatch inclued in this repository

```
docker run -it --rm -p 13209:13209 doomsday -game doom1-share -p /app/autoexec.cfg -iwad /app -port 13209 -stdout
```

Run this container by using a volume mount of the local directory containing a `autoexec.cfg` and WADS

```
docker run -it --rm -p 13209:13209 -v `pwd`:/app doomsday -game doom1-share -p /app/autoexec.cfg -iwad /app -port 13209 -stdout
```

Update the command line options to meet the game type, port etc. See the [Doomsday Multiplayer Server](http://wiki.dengine.net/w/Multiplayer_server) for additional options and configuration.
