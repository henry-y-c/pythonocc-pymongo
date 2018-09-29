# pythonocc-pymongo

A pythonocc + pymongo driver docker image with Python 3 Jupyter Notebook on Debian

[Docker Hub link](https://hub.docker.com/r/henryc/pythonocc-notebook/)

## Usage

1. Start MongoDB server container

```
$ docker run --rm -it -v /absolute/path/to/database/dir:/data/db -p 27017:27017 henryc/mongodb-alpine mongod --bind_ip 0.0.0.0
```

2. Start pythonocc-mongo container

```
$ docker run --rm -it -p 8080:8888 -v /absolute/path/to/notebook/dir:/opt/notebooks henryc/pythonocc-mongo
```

- If you want to run the jupyter notebook using another port on your host OS, change the port number 8080.

- The path for volume mounting should be absolute path.

- To access the MongoDB container from python container, you can directly use the IP address within the default Docker network. Get the MongoDB container's IP address with following command:

  ```
  $ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mongodb-container-name-or-id
  ```
