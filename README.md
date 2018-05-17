* An assorted collection of Dockerfiles, mostly designed for home server/lab
  use. Build/run instructions are in each subdirectory. Bold items are ones that
  I currently use. Others could potentially be out of date. I prefer when
  possible to build my own Docker images rather than pull images build by
  someone else. The only exceptions are `official` images that are vetted by
  Docker and the Plex image (because I trust the company and pay them money for
  support).

  - **Check-MK** (Monitoring system based on Nagios.)
  - **Couchpotato**
  - **Deluge**
  - **Gollum** personal Wiki
  - Headphones
  - **Lazy Librarian**
  - **Media tools** (collection of common tools for working with media files)
  - **OpenVPN-client-pia** (OpenVPN for PIA with port forwarding)
  - **Plex** (Only using the official Plex Docker image now.)
  - **Rsync** (used for backing up Docker data-only volumes)
  - **Sabnzbd**
  - **Samba**
  - **Sickrage**
  - **Socks-proxy** (ssh server for use as a SOCKS proxy to the OpenVPN-client-pia container)
  - **Stringer** (Web-based RSS Reader)
  - **Syncthing**
  - **Traefik** (Configuration notes for the official Traefik image.)
  - **Transmission**

* The standard UID:GID for the containers that don't run as root is 22000:100.
  Make sure to update UID/GID as necessary if you have shared data and need it
  to be easily accessible between containers/host * MIT License

* I use data-only volumes frequently in place of regular volumes due to the
  difficulty of changing ownership of a standard Docker volume. To generate the
  empty `myscratch` image used to create data-only volumes, just use this
  Dockerfile:

        FROM scratch
        LABEL maintainer="<name> <email>"

  Then:

        docker build -t myscratch .
