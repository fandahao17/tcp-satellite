# tcp-satellite

TCP congestion control for satellite network. Tested on Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-89-generic x86_64).

## How to run

Install kernel module management commands:

``` bash
sudo apt-get install build-essential kmod
```

Install kernel headers:

``` bash
sudo apt-get install linux-headers-$(uname -r)
```

Build this module:

``` bash
make
```

Now you should see `tcp_satellite.ko` in this directory. Then load this module:

``` bash
sudo insmod tcp_satellite.ko
```

You can check the module is successfully loaded:

``` bash
sudo lsmod | grep tcp_satellite
```

Then, you can use the following command to change the congestion control algorithm on your machine.

``` bash
sudo sysctl net.ipv4.tcp_congestion_control=satellite
```

Use this command to check your current congestion control algorithm:

``` bash
cat /proc/sys/net/ipv4/tcp_congestion_control
```