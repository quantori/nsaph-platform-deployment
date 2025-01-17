# NSAPH Data Platform (Infrastructure as a Code)
                                 
This platform is based on a deployment for CWL-Airflow developed
by Harvard FAS RC in collaboration with Forome Association.

Essentially, this is a fork of: 
[Apache Airflow + CWL in Docker with Optional Conda and R](https://github.com/ForomePlatform/airflow-cwl-docker)

## Prerequisites 

>**NB**: The docker-compose.yaml in this project uses profiles and therefore
> requires **docker-compose utility version 1.29+**
                    
## Installation

[Deployment Guide](docs/Guide.md) provides detailed information about
deployment options and custom configurations.

[Howto](docs/Howto.md) provides a list of required and optional steps
that should be performed during the deployment.  

Installation of CWL-Airflow on a dedicated host is relatively simple and 
is by and large covered by the [Quick Start](#quick-start) section below.

Advanced options are described in the 
[Configuration Guide](docs/Configuration.md)

> If the host where you are installing CWL-Airflow is shared with other 
> applications, especially those, using PostgreSQL, you should carefully read 
> [Howto](docs/Howto.md) and [Configuration Guide](docs/Configuration.md)
 
After you have deployed CWL-Airflow, 
[test it](docs/Testing.md) 
with the included examples.
                         
You should be aware of some [useful commands](docs/UsefulCommands.md).


## Quick Start
 
This quick start is specific to NSAPH project. For testing general 
platform capabilities please refer to original 
[CWL-Airflow deployment README](https://github.com/ForomePlatform/airflow-cwl-docker#quick-start)

Full sequence of commands to copy and paste for  a clean VM:

    git clone https://github.com/NSAPH-Data-Platform/nsaph-platform-deployment.git
    cd nsaph-platform-deployment
    git submodule update --init --recursive
    DOCKER_BUILDKIT=1 BUILDKIT_PROGRESS=plain docker-compose --env-file ./.env build
    mkdir -p ./dags && cp -rf ./project/examples/* ./dags
    docker-compose --env-file ./.env up -d
    
                                                  
The whole process, when using a stable Internet
connection should take from 20 minutes to a few hours depending on your 
Internet speed.
                 
You can test the installation as described in 
[Testing the installation](docs/Testing.md) section. The first two 
examples should run in both command-line mode and in Airflow UI. 
The third example requires Conda.


## Testing 

Testing is described in the [Test Guide](docs/Testing.md).
