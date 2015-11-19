---
layout: post
title: Configuring realtime with Ardour3 and Ubuntu 14
date: 2015-08-21 21:41:29.000000000 +02:00
type: post
published: true
status: publish
categories:
- Non classé
tags: []

---
{% highlight sh %}
sudo cp /etc/security/limits.d/audio.conf.disabled /etc/security/limits.d/audio.conf
usermod  -a -G audio [user]
{% endhighlight %}
Then restart the computer.
<p>&nbsp;</p>
