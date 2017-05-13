`dmesg` output on disk insert:

```
[  939.462801] sr 2:0:0:0: [sr0] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  939.462814] sr 2:0:0:0: [sr0] tag#1 Sense Key : Medium Error [current]
[  939.462821] sr 2:0:0:0: [sr0] tag#1 Add. Sense: No seek complete
[  939.462830] sr 2:0:0:0: [sr0] tag#1 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  939.462836] blk_update_request: I/O error, dev sr0, sector 0
[  943.174144] sr 2:0:0:0: [sr0] tag#4 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  943.174158] sr 2:0:0:0: [sr0] tag#4 Sense Key : Medium Error [current]
[  943.174166] sr 2:0:0:0: [sr0] tag#4 Add. Sense: Unrecovered read error
[  943.174175] sr 2:0:0:0: [sr0] tag#4 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  943.174181] blk_update_request: I/O error, dev sr0, sector 0
[  943.174189] Buffer I/O error on dev sr0, logical block 0, async page read
[  946.429595] sr 2:0:0:0: [sr0] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  946.429609] sr 2:0:0:0: [sr0] tag#7 Sense Key : Medium Error [current]
[  946.429616] sr 2:0:0:0: [sr0] tag#7 Add. Sense: Read retries exhausted
[  946.429625] sr 2:0:0:0: [sr0] tag#7 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  946.429631] blk_update_request: I/O error, dev sr0, sector 0
[  946.429640] Buffer I/O error on dev sr0, logical block 0, async page read
```

Then `Read retries exhausted` is repeaded, with tag#N increased by 3 up to 28,
- then reseted to 0, up to 30,
- then reseted to 2, up to 29,
- then reseted to 1, up to 28,
- and so on.

Error message meaning:
- https://en.wikipedia.org/wiki/Key_Code_Qualifier

# `smartctl` output

```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-77-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               Optiarc
Product:              BD ROM BC-5540H
Revision:             1.B0
User Capacity:        432,734,208 bytes [432 MB]
Logical block size:   2048 bytes
Device type:          CD/DVD
Local Time is:        Thu May 11 00:55:47 2017 +03
SMART support is:     Unavailable - device lacks SMART capability.

=== START OF READ SMART DATA SECTION ===

Error Counter logging not supported

Device does not support Self Test logging
```

# `dd conv=noerror`

```
time dd conv=noerror if=/dev/sr0 of=2016.iso
dd: error reading '/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes copied, 9.23642 s, 0.0 kB/s
```

... and so on, repeatedly.

From `dmesg` output, it could be seen, that `dd` tries to read each sector
eight times. Then it increments logical block under read by 1 and sector under read by 8.

Not a single byte copied in six minutes.

- https://serverfault.com/questions/407007/what-do-these-disk-errors-in-syslog-mean

# Open DVD disk using VLC

```
libdvdnav: Using dvdnav version 5.0.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
```

Which means, install `libdvd-pkg` in Ubuntu 16.04.
