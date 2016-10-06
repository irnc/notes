## Remove outdated Ubuntu package

Latest release of Ubuntu [packages version `1.5.2-1`][1], which does not support
docker-compose file version 2.

[1]: http://packages.ubuntu.com/search?suite=yakkety&searchon=names&keywords=docker-compose

`sudo apt remove docker-compose`

## Install newest `docker-compose`

Follow instructions from https://docs.docker.com/compose/install/.

Basically go to [releases page][2] and copy-paste `curl` and `chmod` commands.

[2]: https://github.com/docker/compose/releases
