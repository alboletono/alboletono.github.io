---
layout:
title: jmx_remote
categories: []
tags: []
published: True

---

To enable the remote jmx without ssl and authentication:
<pre>
-Dcom.sun.management.jmxremote.port=4711 -Dcom.sun.management.jmxremote.authenticate=false
  -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.ssl=false
</pre>

Be careful to have a correct hostname, check with:
<pre>
    hostname -i
</pre>

If you have localhost interface, you shall set your IP address like the following:
<pre>
    -Djava.rmi.server.hostname=[IP addresse]
</pre>
