# doomsday
Docker Container for [Doomsday Engine Multiplayer Server](https://manual.dengine.net/multiplayer/running_a_server).

Dockerfile builds the following,

- Ubuntu 18.04 and packages to run Doomsday
- Downloads and installs Doomsday
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

## Known Issues

- Running the container without any arguments will not work, even if they're in the Dockerfile `CMD` statement. Workaround is to pass them in `docker run`
- Ctrl-C to stop the container will not work, and the running container must be killed with `docker rm -f`
