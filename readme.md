# JBake docker

Unofficial Docker Image for [JBake](http://jbake.org/).

Simple try

```
docker run --rm -it jeci/jbake-docker
```

To bake locale blog, first init jbake

```
mkdir data
docker run --rm -v $PWD/data:/data -t jeci/jbake-docker -i
```

make your change in `data` then build

```
docker run --rm -v $PWD/data:/data -t jeci/jbake-docker -b
ls data/output
```

Test with embebded jetty and go to http://localhost:8820/

```
docker run --rm -v $PWD/data:/data --net=host -t jeci/jbake:2.4.0
```


finaly deploy to your own server

```
rsync -az data/output/ server:/var/www/html/
```
