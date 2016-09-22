I need to run [JOSM][2] on Ubuntu.

[2]: https://josm.openstreetmap.de/

Easiest way seems to use [JNLP file][3], instead of downloading `.jar` file.

[3]: https://josm.openstreetmap.de/download/josm.jnlp

Ok, I know that is is Java Web Start, so I [lookup for `javaws`][1]. Which
gives me an `icedtea-netx` package.

[1]: http://packages.ubuntu.com/search?suite=xenial&section=all&arch=any&keywords=javaws&searchon=contents

```sh
sudo apt install icedtea-netx
```

Now it works perfectly fine on Ubuntu 16.04 LTS.

```sh
javaws https://josm.openstreetmap.de/download/josm.jnlp
```
