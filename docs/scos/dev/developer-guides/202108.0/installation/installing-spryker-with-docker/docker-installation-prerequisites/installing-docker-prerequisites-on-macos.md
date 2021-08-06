---
title: Installing Docker prerequisites on MacOS
originalLink: https://documentation.spryker.com/2021080/docs/installing-docker-prerequisites-on-macos
redirect_from:
  - /2021080/docs/installing-docker-prerequisites-on-macos
  - /2021080/docs/en/installing-docker-prerequisites-on-macos
---

This article describes Docker installation prerequisites for MacOS.


## Minimum system requirements

Review the minimum system requirements in the table:

| System Requirement | Additional Details |
| --- | --- |
| vCPU: 2 | This is a minimum requirement. The value can be higher than 2. A lower value is not sufficient for running the application. |
| RAM: 4GB | This is a minimum requirement. The value can be higher than 4GB. A lower value is not sufficient for installation purposes. |
| Swap: 2GB | This is a minimum requirement. The value can be higher than 2GB. A lower value is not sufficient for installation purposes. |


## Installing and configuring required software
Follow the steps to install and configure the required software:
1. Download and install [Docker Desktop (Mac)](https://desktop.docker.com/mac/stable/amd64/Docker.dmg).
2. Accept the privilege escalation request "Docker Desktop needs privileged access.".
{% info_block infoBox %}
Signup for Docker Hub is not required.
{% endinfo_block %}

3. Go to ![whale](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Installation/Spryker+in+Docker/Docker+Install+Prerequisites+-+MacOS/whale-x.png) > **Preferences**  > **Command Line** and **Enable experimental features**.


4. Update Memory and Swap Limits:

    1. Go to![whale](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Installation/Spryker+in+Docker/Docker+Install+Prerequisites+-+MacOS/whale-x.png) > **Preferences**  > **Resources** > **ADVANCED**.
    2. Set **CPUs:** to "4" or higher.
    3. Set **Memory:** to "4.00 GB" or higher.
    4. Set **Swap:** to "2.00 GB" or higher.
    5. Set the desired **Disk image size:**.
    6. Select the desired **Disk image location**.
    7. Click **Apply & Restart**. 

{% info_block warningBox %}
You can set lower **Memory:** and **Swap:** limit values. However, the default limits won't be sufficient to run the application, so make sure to increase them. 
{% endinfo_block %}

5. [Development mode](https://documentation.spryker.com/docs/modes-overview#development-mode): Install Mutagen:
```shell
brew install mutagen-io/mutagen/mutagen-beta
```

## Next steps

See [Chossing an installation mode](https://documentation.spryker.com/docs/choosing-an-installation-mode) to choose an installation mode.
If you've already selected an installation mode, follow one of the guides below:
* [Installing in Development mode on MacOS and Linux](https://documentation.spryker.com/docs/installing-in-development-mode-on-macos-and-linux)
* [Installing in Demo mode on MacOS and Linux](https://documentation.spryker.com/docs/installing-in-demo-mode-on-macos-and-linux)
* [Integrating Docker into existing projects](https://documentation.spryker.com/docs/integrating-docker-into-existing-projects)
* [Running production](https://documentation.spryker.com/docs/running-production)


