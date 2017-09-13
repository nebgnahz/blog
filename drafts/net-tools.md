Network Tools
---

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [-](#-)
- [[Wondershaper](http://lartc.org/wondershaper)](#wondershaperhttplartcorgwondershaper)
- [[Netstat](http://www.tldp.org/LDP/nag2/x-087-2-iface.netstat.html)](#netstathttpwwwtldporgldpnag2x-087-2-ifacenetstathtml)
    - [Routing](#routing)
- [Clockdiff](#clockdiff)
- [NTP](#ntp)

<!-- markdown-toc end -->

Here is a quick dump of network-related tools (diagnose, monitoring, alteration,
etc).

# [Wondershaper](http://lartc.org/wondershaper)

An advanced tool is `tc` but wondershaper is easy enough to use (and often suffice your purpose of throttling the bandwidth).

```shell
## wondershaper [interface] [downlink] [uplink]
sudo wondershaper wlan0 512 128

## wondershaper clear [interface]
sudo wondershaper clear wlan0
```

# [Netstat](http://www.tldp.org/LDP/nag2/x-087-2-iface.netstat.html)

`netstat` is often too powerful to master what you can do with it. Let's take an example-driven approach below.

## Routing

Show kernel routing table. This is super helpful if you are working with Docker or VM and need to setup a local subnet.
For example, on my machine, docker creates a virtual interface `docker0` and takes the subnet of `172.17.0.0/16`.

```shell
$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         128.32.171.1    0.0.0.0         UG        0 0          0 enp0s25
128.32.171.0    0.0.0.0         255.255.255.0   U         0 0          0 enp0s25
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0
```

# Clockdiff

One of the question I ask when doing distributed computing is "how can I measure
latency." If the clocks on two hosts are the same, then this can be trivial:
diff the timestamp. But that's a big "if".

This tool tells the clock difference between two hosts, in millisecond level
accuracy.

```shell
$ clockdiff 54.153.118.87
host=54.153.118.87 rtt=50(0)ms/50ms delta=-1ms/-1ms Wed Sep 13 17:45:11 2017
```

# NTP

Use NTP suite to loosely synchronize two machines to the same server.

```shell
$ sudo service ntp stop
$ sudo ntpdate -s ntp.ubuntu.com
$ sudo service ntp start
$ ntpq -p
    remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 0.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 1.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 2.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 3.ubuntu.pool.n .POOL.          16 p    -   64    0    0.000    0.000   0.000
 ntp.ubuntu.com  .POOL.          16 p    -   64    0    0.000    0.000   0.000
 clock2.xmission .XMIS.           1 u    1   64    1   56.882    4.915   0.009
 199.102.46.78 ( .GPS.            1 u    1   64    1   27.731    4.903   0.062
 pacific.latt.ne 44.24.199.34     3 u    1   64    1   64.339   -1.063   0.000
 dbsquared.com   38.229.71.1      3 u    -   64    1   58.192  -171.55   0.629
 zombie.frizzen. 28.65.181.206    3 u    -   64    1   66.143   -0.069   0.000
 chl.la          127.67.113.92    2 u    -   64    1   74.281   -1.996   1.789
 time-c.nist.gov .NIST.           1 u    1   64    1   32.799   -0.680   0.000
```
