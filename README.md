# random_dockers

Collection of Dockerfiles for various purposes

Docker images can be built directly via GitPod and then pushed manually to DockerHub, e.g.:

```bash

cd <folder_with_docker_file_and_env_yml>
docker build -t atpoint/repo_at_dockerhub:tag .
docker push atpoint/repo_at_dockerhub:tag

```

## Micromamba

There is now also a [micromamba](https://github.com/mamba-org/micromamba-docker) base image that is much smaller than the condaforge/mambaforge image (about 95Mb rather about 415Mb). A Dockerfile for micromamba could be:

```bash

FROM mambaorg/micromamba:0.15.3

COPY --chown=micromamba:micromamba ./environment.yml /tmp/env.yaml

USER root

RUN apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y --no-install-recommends tzdata wget nano && \
    apt-get clean

RUN micromamba install -y -n base -f /tmp/env.yaml && \
    micromamba clean --all --yes
    
```
