# Running MongoDB server

Run MongoDB server inside a container named `mongo-server` using `mongo` image:

`docker run --name mongo-server -d mongo`

# Open `mongo` shell connected to MongoDB server

Run temporary container hosting `mongo` shell connected to MongoDB server running inside `mongo-server` container:

```sh
docker run
  --rm # temporary
  --link mongo-server:m # link to mongo-server
  -it
  mongo # image
  mongo mongodb://m # custom entrypoint to run mongo shell
```

`docker run --rm --link mongo-server:m -it mongo mongo mongodb://m`

Review available databases by running `show dbs` using `mongo` shell.

# Restoring database from dump

```sh
docker run
  --rm
  --link mongo-server:m
  -it
  -v `pwd`/dump:/tmp/dump # connect volume containing dump data
  mongo mongorestore /tmp/dump --host m # restore connected dump into `m` server
```

`docker run --rm --link mongo-server:m -it -v `pwd`/dump:/tmp/dump mongo mongorestore /tmp/dump --host m`

# Running Node.js app connecting to MongoDB server

Create `Dockerfile`:

```
FROM node

WORKDIR /opt/app
COPY package.json .
RUN npm install
COPY app.js .
CMD node app.js
```

Change `app.js` to use `process.env.MONGO_URL`.

Build image: `docker build . --tag hw1-2`.

Run Node.js app connected to previously run `mongo-server` container running MongoDB server:

`docker run --rm --link mongo-server:m -e MONGO_URL="mongodb://m/m101" hw1-2`

## Running express app with views

- Add `COPY views views` below `app.js` copy.
- Expose port 3000 from a container as a port number 4000 locally.
- Add `-it` options so you could `Ctrl+C` express app.

`docker run --rm --link mongo-server:m -e MONGO_URL="mongodb://m/m101" -p 4000:3000 -it hw1-3`
