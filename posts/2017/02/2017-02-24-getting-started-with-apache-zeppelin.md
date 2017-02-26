- follow Quick Start guide
  - https://zeppelin.apache.org/docs/0.7.0/install/install.html
  - download Zeppelin
  - try to verify using `md5sum -c FILE.md5`

```
md5sum -c zeppelin-0.7.0-bin-all.tgz.md5
md5sum: zeppelin-0.7.0-bin-all.tgz.md5: no properly formatted MD5 checksum lines found
```

OK, compare manually.

```
md5sum zeppelin-0.7.0-bin-all.tgz
330484bfd528ff8868e48d4e4e474d94  zeppelin-0.7.0-bin-all.tgz
cat zeppelin-0.7.0-bin-all.tgz.md5
zeppelin-0.7.0-bin-all.tgz: 33 04 84 BF D5 28 FF 88  68 E4 8D 4E 4E 47 4D 94
```

- unpack
- `./bin/zeppelin-daemon.sh start` says `Zeppelin start [  OK  ]` but no server
  listening on :8080
- tail -f logs/zeppelin-*.log, notice that it is still starting
- wait for around 2 minutes and 18 seconds
- go to http://localhost:8080/
- Welcome to Zeppelin!
