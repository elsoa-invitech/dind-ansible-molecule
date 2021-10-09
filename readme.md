# dind-ansible-molecule

[![pipeline status](https://gitlab.com/richardskumat/dind-ansible-molecule/badges/master/pipeline.svg)](https://gitlab.com/richardskumat/dind-ansible-molecule/commits/master)


Based on qwe1/debdocker, because:

- I decided to build this image because I've had some python issues due to upstream
docker:stable being an Alpine image while doing molecule tests
on my Ansible roles.

The image has:

- docker, ansible and molecule installed

I use this image to test molecule converge and test my ansible roles.

There's no entrypoint set in the images, only CMD
is set to bash.

## Tags

The latest/$ANSIBLE_VERSION tag runs as [uid 1000 and is part of the docker group(gid 998.)](https://gitlab.com/richardskumat/dind-ansible-molecule/-/blob/master/Dockerfile).

## Usage examples

Interactive usage, if we are in an Ansible role directory:

```bash
docker run -w /tmp/$(pwd | awk -F'/' '{print $NF}') -v /var/run/docker.sock:/var/run/docker.sock -v $PWD:/tmp/$(pwd | awk -F'/' '{print $NF}') --rm -ti qwe1/dind-ansible-molecule bash
```

Example molecule test, if we are in an Ansible role root directory:

```bash
docker run -w /tmp/$(pwd | awk -F'/' '{print $NF}') -v /var/run/docker.sock:/var/run/docker.sock -v $PWD:/tmp/$(pwd | awk -F'/' '{print $NF}') --rm -ti qwe1/dind-ansible-molecule molecule test
```

## Links to source code and build logs

Gitlab

https://gitlab.com/richardskumat/dind-ansible-molecule

Gitlab pipelines

https://gitlab.com/richardskumat/dind-ansible-molecule/pipelines

Github

https://github.com/richardskumat/dind-ansible-molecule

Dockerhub

https://hub.docker.com/r/qwe1/dind-ansible-molecule