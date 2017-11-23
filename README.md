# Prerequisites

This repository includes assets that make use of the Large File Storage (LFS) extensions for `git`. In order to properly clone the repository and run the container, you will need to install `git-lfs` in the host environment.

___NOTE:__ `git-lfs` requires version 1.8.2 or later of `git`. You can check which version is currently installed by running `git --version`.

```bash
brew install git # (Optional) Install the latest version of git using Homebrew on macOS

brew install git-lfs # Install to git-lfs system using Homebrew on macOS

git lfs install # Configure git for LFS repositories
```

The repository includes Docker configuration to launch a copy of Lucee 5 within a Docker container. 

[Download](https://store.docker.com/editions/community/docker-ce-desktop-mac) and run the Docker Community Edition installer from the Docker Store.

# Environment

Modify the `/etc/hosts` file on the local system to resolve the sandbox.local domain name to 127.0.0.1.

```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1             localhost
127.0.0.1       sandbox.local
```
Create a .env file in the root of the directory defining the following required variables for your local environment, modifying the values to suit your requirements.

```
LUCEE_PASSWORD=password
MYSQL_ROOT_PASSWORD=password
MYSQL_HOST=appdb
MYSQL_DATABASE=test
AWS_PROFILE=default
AWS_REGION=us-west-2
```

# Application

Lucee will map the _sandbox.local_ hostname to `./sites/www/public`, meaning the `application.cfc` and `index.cfm` should be created at this location. 

Launch the local hosting environment using `docker-compose`:

```bash
docker-compose up # Launch the specified service containers
```

When making modifications to the server configuration, e.g, introducing new Java dependencies outside of the source path, you will need to instruct Docker to rebuild the services:

```bash
docker-compose build # Force Docker to rebuild the container with dependencies
```
