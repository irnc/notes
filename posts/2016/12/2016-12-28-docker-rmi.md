# Digital Footprint Clean-up Check

Following a good practice of [cleaning up before New Year][], developers should
clean not only their inboxes, but also local machines, e.g. from Docker images.

[cleaning up before New Year]: https://www.facebook.com/smashmag/photos/a.421623662489.198486.45576747489/10154921148452490/?type=3&theater

First I tried to remove known outdated images specifically, but then I realized,
that on my machine there was a lot of images tagged `<none>:<none>`. No
repository or tag, only image id and an indication that they was created months
ago.

So why bother, let's delete all Docker images at once:

```sh
docker rmi -f $(docker images | grep MB | awk '{ print $3 }')
```

Note that it is good to know some shell magic, because there is
[no support for wildcards][] in Docker.

[no support for wildcards]: https://github.com/docker/docker/issues/17237

## Side note: where `<none>:<none>` images are coming from

`<none>:<none>` images are coming from `docker-compose` building a service
using a `Dockerfile`. Each command from `Dockerfile` creates an intermediate
image leaved as cache to be reused by consecutive builds.

If parent image is still available, those untagged images would be removed by
`docker-compose down --rmi local`. If parent image was rebuild, i.e. under the
same name, there is different image now, the quickest way to remove these
untagged images is to [remote the top-most one][], all other will be pruned:

```sh
docker rmi $(docker images -f "dangling=true" -q)
```

[remote the top-most one]: http://www.projectatomic.io/blog/2015/07/what-are-docker-none-none-images/
