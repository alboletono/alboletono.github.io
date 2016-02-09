---
layout:
title: Ubuntu lan card disconnected
categories: []
tags: []
published: True

---

Most of the time I have problems to install wifi cards. But THIS time this was etherned lan card!

By tailing my syslog I saw that the card was connected/disconnected in loop.

{% highlight bash %}
e1000e: eth0 NIC Link is Down
<info> (eth0): carrier now OFF (device state 30)
<info> (eth0): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
<info> (eth0): deactivating device (reason 'carrier-changed') [40]
<info> (eth0): carrier now ON (device state 20)
<info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
{% endhighlight %}

The solution in fact was to download the last module source from intel web site and install it :
{% highlight bash %}
wget https://downloadcenter.intel.com/downloads/eula/15817/Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-?httpDown=https%3A%2F%2Fdownloadmirror.intel.com%2F15817%2Feng%2Fe1000e-3.3.3.tar
tar -xvf e1000e-3.3.3.tar
cd e1000e-3.3.3/src
sudo make install
sudo rmmod e1000e
sudo insmod e1000e.ko
sudo ifdown eth0
sudo ifup eth0
{% endhighlight %}

And voilà!
