# Config-Server

Config server is an implementation of spring cloud config server. It provides externalisation for clients on the cloud native applications.


## Building the docker image

In order to build the config server you need to issue following command

```shell
$ mvn clean install dockerfile:build
```


### Pushing the Docker Image

In order to build the config server you need to issue following command

```shell
$ mvn dockerfile:push
```

### Running the Docker Container

You can run the docker container for config server using following command

```shell
$ docker run -p 8888:8888 -it shopping/config-server
```

### Test the config server
Once docker is running, in order to check if config server is running on your machine issue following command

```shell
curl http://localhost:8888/catalog-service/default
```

You should see output like this:

```json
{"name":"catalog-service","profiles":["default"],"label":null,"version":"4a704ececebe07dd609f334360361f642f45fe80","state":null,"propertySources":[{"name":"https://github.com/khurramsyed/microservices-example/config/catalog-service/application.yml","source":{"test.property":"Hello"}}]}
```


### Enable Debugging for applications inside docker container


```shell
$ docker run -e "JAVA_OPTS=-agentlib:jdwp=transport=dt_socket,address=5005,server=y,suspend=n" -p 8888:8888 -p 5005:5005 -t shopping/config-server

```

#### Note
This readme was generated using docker for mac, please create an issue on git if docker does not run on your system.