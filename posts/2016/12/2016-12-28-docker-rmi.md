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
