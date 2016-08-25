# JBake docker

Unofficial Docker Image for [JBake](http://jbake.org/).

## Quick Start

```bash
docker run --rm -it --net=host jeci/jbake-docker
```

Then go http://localhost:8820/

## Bake your own

### first init jbake

```bash
mkdir jbake_sample
docker run --rm -v $PWD/jbake_sample:/data -t jeci/jbake-docker -i
```

### Bake

Make your change in `jbake_sample` then build :

```bash
docker run --rm -v $PWD/jbake_sample:/data -t jeci/jbake-docker -b
ls data/output
```

## Preview

Test with embebded jetty and go to http://localhost:8820/

```bash
docker run --rm -v $PWD/jbake_sample:/data --net=host -it jeci/jbake-docker -s
```

## Deploy

Finaly deploy to your own server with simple rsync.

```bash
rsync -az jbake_sample/output/ example.org:/var/www/html/
```

## Faster

Without parameter, docker run `jbake -b -s`, so in my own project I did :

```bash
cd www.example.org
docker run -v $PWD:/data --net=host --name=jbake --rm -it jeci/jbake-docker
```

If you build / test often, start server in detach mode.

```bash
cd www.example.org
docker run -v $PWD:/data --net=host --name=jbake -dt jeci/jbake-docker

// work
docker run -v $PWD:/data --rm -it jeci/jbake-docker -b
// work more
docker run -v $PWD:/data --rm -it jeci/jbake-docker -b

// ending
docker stop jbake
docker rm jbake
```

But in reality I'm not running jbake on my computer, I use gitlab-ci to build and
deploy my site automaticaly.
