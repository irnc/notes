```sh
docker run --name mongod -d mongo
docker run --rm -it --link mongod:mongo mongo mongo mongodb://mongo
```

```sh
docker run --rm -it --link mongod:mongo -v `pwd`/dump:/dump mongo mongorestore /dump --host mongo
```
