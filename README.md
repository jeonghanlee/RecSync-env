# RecSync-env
[![Debian 11](https://github.com/jeonghanlee/RecSync-env/actions/workflows/debian11.yml/badge.svg)](https://github.com/jeonghanlee/RecSync-env/actions/workflows/debian11.yml)

[![Rocky8](https://github.com/jeonghanlee/RecSync-env/actions/workflows/rocky8.yml/badge.svg)](https://github.com/jeonghanlee/RecSync-env/actions/workflows/rocky8.yml)

Configuration Environment for the recsync server (aka. RecCeiver) at <https://github.com/ChannelFinder/recsync/tree/master/server>

## Pre-required Packages

### Debian 12

```
apt install git make sudo tree python3-twisted  python3-simplejson  python3-urllib3 python3-requests
```


```bash
make setup.deb
```

```
make init
make conf
make conf.show
make install
make sd_start
make sd_status
```


```
make init
make local.conf
make local.conf.show
make local.install
make exist
make local.run
make local.stop
make local.status
```

## macOS

We only support macOS for testing and developing purposes, so we don't have launchd configuration. We localize the recsync service within a local folder, and define several simple Makefile rules to maintain them.
To use the following rules, one need to setup `homebrew` first.

* Install Python3 and its required packages through `pip3`

```bash
make install.p3mac
```

* Installation and running procedures

```
make init
make conf
make conf.show
make local.install
make exist
make local.run
make local.stop
```

The log file will be located in `RS_INSTALL_LOCATION`, e.g., `$(TOP)/recsync.local` folder, which can be checked through `make local.status`. And one can remove all local directory through `make local.rm`

## Docker Image

* The Docker image is hosted at https://hub.docker.com/orgs/alscontrols.
* See [docs/Docker.md](docs/Docker.md) :whale:

## While evaluating its configuration

Modify any configuration files, and then run the following command:

```bash
make restart
sudo systemctl start recsync.service
systemctl status recsync.service
```

## Reference

[1] <https://github.com/ChannelFinder/pyCFClient>

[2] <https://github.com/ChannelFinder/recsync>

[3] <https://epics-controls.org>
