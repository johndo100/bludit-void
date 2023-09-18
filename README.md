# Yet Another Bludit Docker Image

This Docker container is what I'm trying to do with other Linux distro for more update and reducing the image size.

Original work is [here](https://github.com/bludit/docker).

Build from Dockerfile by docker or buildah.

It powered by:
- [Void](https://voidlinux.org)
- [Bludit](https://www.bludit.com)
- [s6-overlay](https://github.com/just-containers/s6-overlay)

~~Other version with [Tini](https://github.com/krallin/tini) init will be availabe soon.~~

A [dinit](https://gitlab.com/tozd/dinit) version will be updated when [dinit](https://gitlab.com/tozd/dinit) became stable.

### Run the container

`$ docker run --name bludit -p 8000:80 -d johndo100/bludit-void`

To get access visit with your browser http://localhost:8000.

### Run the container and mounting a volume to persist data

```
mkdir ~/bludit

docker run --name bludit \
    -p 8000:80 \
    -v ~/bludit:/usr/share/nginx/html/bl-content \
    -d johndo100/bludit-void:latest
```

### Run the container and mount volumes to persist themes & plugins

```
mkdir ~/bludit
mkdir ~/bludit-themes
mkdir ~/bludit-plugins

docker run --name bludit \
    -p 8000:80 \
    -v ~/bludit:/usr/share/nginx/html/bl-content \
    -v ~/bludit-themes:/usr/share/nginx/html/bl-themes \
    -v ~/bludit-plugins:/usr/share/nginx/html/bl-plugins \
    -d johndo100/bludit-void
```

To get access visit with your browser http://localhost:8000.

Tested by [Podman](https://podman.io) on [Void (Linux)](https://voidlinux.org) desktop.
