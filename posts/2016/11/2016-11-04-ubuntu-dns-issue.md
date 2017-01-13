```
pavel@pavel-202:~$ tail -n 1000 -f /var/log/syslog | grep -i dnsmasq
Nov  4 09:49:05 pavel-202 NetworkManager[1097]: <info>  [1478242145.6765] dns-mgr[0x12748b0]: set resolv-conf-mode: dnsmasq, plugin="dnsmasq"
Nov  4 09:49:10 pavel-202 NetworkManager[1097]: <info>  [1478242150.3601] dns-plugin[0x12707a0]: starting dnsmasq...
Nov  4 09:49:10 pavel-202 NetworkManager[1097]: dnsmasq: unknown interface docker0
Nov  4 09:49:10 pavel-202 dnsmasq[1330]: unknown interface docker0
Nov  4 09:49:10 pavel-202 dnsmasq[1330]: FAILED to start up
Nov  4 09:49:21 pavel-202 NetworkManager[1097]: <warn>  [1478242161.3301] dnsmasq[0x12707a0]: dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Nov  4 09:49:21 pavel-202 NetworkManager[1097]: <warn>  [1478242161.4299] dns-mgr: plugin dnsmasq child quit unexpectedly
```

```
$ netstat -nul|grep :53
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 :::5353                 :::*
```

```
● NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Пят 2016-11-04 09:49:05 +03; 10min ago
 Main PID: 1097 (NetworkManager)
    Tasks: 4
   Memory: 15.3M
      CPU: 438ms
   CGroup: /system.slice/NetworkManager.service
           ├─1097 /usr/sbin/NetworkManager --no-daemon
           └─1313 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-7cd98e4c-dffc-4c90-b0ba-81b096562088-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
```

---

```sh
sudo service NetworkManager restart
```

TK show output of `tail -f /var/log/syslog | grep -i dnsmasq` after restart.

```
● NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Пят 2016-11-04 10:01:08 +03; 2min 34s ago
 Main PID: 6107 (NetworkManager)
    Tasks: 5
   Memory: 16.1M
      CPU: 303ms
   CGroup: /system.slice/NetworkManager.service
           ├─6107 /usr/sbin/NetworkManager --no-daemon
           ├─6129 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
           └─6148 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-eth0.pid -lf /var/lib/NetworkManager/dhclient-7cd98e4c-dffc-4c90-b0ba-81b096562088-eth0.lease -cf /var/lib/NetworkManager/dhclient-eth0.conf eth0
```

```
$ netstat -nul|grep :53
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 127.0.1.1:53            0.0.0.0:*                          
udp        0      0 127.0.0.1:53            0.0.0.0:*                          
udp        0      0 172.17.0.1:53           0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 ::1:53                  :::*                               
udp6       0      0 fe80::42:18ff:fe17:b:53 :::*
```
