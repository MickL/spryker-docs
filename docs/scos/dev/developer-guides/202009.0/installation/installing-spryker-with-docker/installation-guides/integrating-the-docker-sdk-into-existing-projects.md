---
title: Integrating the Docker SDK into existing projects
originalLink: https://documentation.spryker.com/v6/docs/integrating-the-docker-sdk-into-existing-projects
redirect_from:
  - /v6/docs/integrating-the-docker-sdk-into-existing-projects
  - /v6/docs/en/integrating-the-docker-sdk-into-existing-projects
---

This page describes how you can convert a non-Docker based project into a Docker based one. If you want to install Spryker in Docker from scratch, start with [Development Mode](https://documentation.spryker.com/docs/modes-overview#development-mode) or [Demo Mode](https://documentation.spryker.com/docs/modes-overview#demo-mode).

## Prerequisites

To start integrating Docker into your project:

1. Follow one of the Docker installation prerequisites:
    * [Installing Docker prerequisites on MacOS](https://documentation.spryker.com/docs/installing-docker-prerequisites-on-macos)
    * [Installing Docker prerequisites on Linux](https://documentation.spryker.com/docs/installing-docker-prerequisites-on-linux)
    * [Installing Docker prerequisites on Windows](https://documentation.spryker.com/docs/installing-docker-prerequisites-on-windows)
2. Integrate the [Spryker Core](https://documentation.spryker.com/docs/spryker-core-feature-integration) feature into your project. 

## Set up .dockerignore

Create a new `.dockerignore` file to match the project file structure:
```yaml
.git
.idea
node_modules
/vendor
/data
!/data/import
.git*
.unison*
/.nvmrc
/.scrutinizer.yml
/.travis.yml
/newrelic.ini

/docker
!/docker/deployment/
```
See [.dockerignore file](https://docs.docker.com/engine/reference/builder/#dockerignore-file) to learn more about the structure of the file.

## Set up configuration

In `config/Shared`, adjust or create a configuration file. The name of the file should correspond to your environment. See  [config_default-docker.php](https://github.com/spryker-shop/b2c-demo-shop/blob/master/config/Shared/config_default-docker.php) as an example. 

Make sure to adjust the configuration for each separate store. See [config_default-docker_DE.php](https://github.com/spryker-shop/b2c-demo-shop/blob/master/config/Shared/config_default-docker_DE.php) as an example.

## Set up a Deploy file

Set up a [Deploy file](https://documentation.spryker.com/docs/deploy-file-reference-10) per your infruscturcure requirements using the examples in the table:

| Development mode | Demo mode |
| --- | --- |
| [B2C Demo Shop deploy file](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.dev.yml) | [B2C Demo Shop deploy file](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.yml) |
| [B2B Demo Shop deploy file](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.dev.yml) | [B2B Demo Shop deploy file](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.yml) |

## Set up the installation script

In `config/Shared`, prepare the installation recipe that defines the way Spryker should be installed.

Use the following recipe examples:
* [B2B Demo Shop installation recipe](https://github.com/spryker-shop/b2b-demo-shop/blob/master/deploy.yml)
* [B2C Demo Shop installation recipe](https://github.com/spryker-shop/b2c-demo-shop/blob/master/deploy.yml)

## Install the Docker SDK
Follow the steps to install the Docker SDK:
1. Fetch Docker SDK tools:
```bash
git clone https://github.com/spryker/docker-sdk.git ./docker
```
{% info_block warningBox "Verification" %}

Make sure `docker 18.09.1+` and `docker-compose 1.23+` are installed:

```bash
$ docker version
$ docker-compose --version
```

{% endinfo_block %}

2. Initialize docker setup:
 ```bash
docker/sdk bootstrap
```
{% info_block infoBox "Bootstrap" %}

Once you finish the setup, you don't need to run `bootstrap` to start the instance. Run it only after:
* Docker SDK version update
* Deploy file update

{% endinfo_block %}
3. Build and run Spryker applications:
```bash
docker/sdk up
```

{% info_block warningBox %}

Ensure that, in the `hosts` file in the local environment, all the domains from `deploy.yml` are defined as `127.0.0.1`.

{% endinfo_block %}


## Endpoints

To ensure that the installation is successful, make sure you can access the configured endpoints from the Deploy file. See [Deploy file reference - 1.0](https://documentation.spryker.com/docs/deploy-file-reference-10) to learn about the Deploy file.

{% info_block infoBox "RabbitMQ UI credentials" %}

To access RabbitMQ UI, use `spryker` as a username and `secret` as a password. You can adjust the credentials in `deploy.yml`.

{% endinfo_block %}



## Getting the list of useful commands

To get the full and up-to-date list of commands, run `docker/sdk help`.

## Next steps
* [Troubleshooting](https://documentation.spryker.com/docs/spryker-in-docker-troubleshooting)
* [Debugging Setup in Docker](https://documentation.spryker.com/docs/debugging-setup-in-docker)
* [Deploy File Reference - 1.0](https://documentation.spryker.com/docs/deploy-file-reference-10) 
* [Services](https://documentation.spryker.com/docs/services)
* [Self-signed SSL Certificate Setup](https://documentation.spryker.com/docs/self-signed-ssl-certificate-setup) 
* [Additional DevOPS Guidelines](https://documentation.spryker.com/docs/additional-devops-guidelines)
