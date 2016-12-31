# Network Tools

Here is a quick dump of network-related tools (diagnose, monitoring, alteration, etc).

## [Wondershaper](http://lartc.org/wondershaper)

An advanced tool is `tc` but wondershaper is easy enough to use (and often suffice your purpose of throttling the bandwidth).

```shell
## wondershaper [interface] [downlink] [uplink]
sudo wondershaper wlan0 512 128

## wondershaper clear [interface]
sudo wondershaper clear wlan0
```

## [Netstat](http://www.tldp.org/LDP/nag2/x-087-2-iface.netstat.html)

`netstat` is often too powerful to master what you can do with it. Let's take an example-driven approach below.

### Routing

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
