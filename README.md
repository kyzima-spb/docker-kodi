# Kodi in Docker

### Volumes

* `/home/user/.kodi` - directory with kodi files.

### Environment Variables

* `XVFB_RESOLUTION` - screen resolution of the virtual X server;
* `VNC_SERVER_PASSWORD` - the password for the VNC server.

### Forwarded ports:
* `5900` - TCP port for connecting VNC clients.

## Run

```bash
docker run --rm -ti --name kodi_1 \
    -p 5900:5900 \
    -v $(pwd)/plugin:/home/user/.kodi/addons \
    kyzimaspb/kodi
```
