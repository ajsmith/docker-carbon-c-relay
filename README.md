# docker-carbon-c-relay

This project provides resources for deploying the Carbon C Relay in Docker on
Fedora and Red Hat Enterprise Linux.


# Base Images

- Fedora 24
- RHEL 7.2


# Requirements

- Docker

- The RHEL version of the image requires an active subscription for Red Hat
  Enterprise Linux Server.


# Building

To build the Fedora image, run:

```.shell
$ docker build -t carbon-c-relay:fedora -f Dockerfile.fedora .
```

To build the RHEL image, run:

```.shell
$ docker build -t carbon-c-relay:rhel -f Dockerfile.rhel .
```


# Running the Container

To launch, run:

```.shell
$ docker run carbon-c-relay
```


# Customizing the Image

The recommended method of customizing the image is to mount your own
configuration files as a volume on the container, as so:

```.shell
$ docker run \
    -v /path/to/custom/carbon-c-relay.conf:/etc/carbon-c-relay.conf:ro \
    carbon-c-relay
```

If SELinux is enabled on your host (and it should be!), you'll also need to
apply the `svirt_sandbox_file_t` type label to your configuration file, as so:

```.shell
$ chcon -t svirt_sandbox_file_t /path/to/custom/carbon-c-relay.conf
```


# Networking

The image exposes port 2003 for client connections.


# Releases


## 1.0

- Initial release of RHEL 7.2 and Fedora 24 images
