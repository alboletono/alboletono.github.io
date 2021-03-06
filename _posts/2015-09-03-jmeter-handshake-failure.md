---
layout: link
title: "JMeter handshake_failure"
categories: []
tags: []
published: True
link: https://blogs.oracle.com/java-platform-group/entry/diagnosing_tls_ssl_and_https
---

By running JMeter scenarios that were working previously on the same site I did get a java "handshake_failure".

Generally (and in my case) it is due to cipher algorithm change. Probably an update or another configuration of the custom apache web site.

Diagnostic
----------

By following the link https://blogs.oracle.com/java-platform-group/entry/diagnosing_tls_ssl_and_https I was able to diagnose and solve the problem.

Important thing is to activate the debug mode for the jvm.
In my jmeter.sh I added:

{% highlight sh %}
JVM_ARGS="-Djavax.net.debug=ssl:handshake:verbose"
{% endhighlight %}

{% highlight sh %}
XXX, WRITE: TLSv1 Handshake, length = 107
XXX, READ: TLSv1 Alert, length = 2
XXX, RECV TLSv1 ALERT:  fatal, handshake_failure
XXX, called closeSocket()
XXX, handling exception: javax.net.ssl.SSLHandshakeException: Received fatal alert: handshake_failure
XXX, called close()
XXX, called closeInternal(true)
Ignoring unsupported cipher suite: TLS_DHE_DSS_WITH_AES_128_CBC_SHA256
{% endhighlight %}

Quick solution
--------------

I was using the jdk 7. By testing the same scenario using jdk 8, that was solved!


Full solution
-------------



If you are not able to update jdk the quick solution is not applicable.
By just looking at the previous log you can see that the cipher algorithm is SHA256withRSA. You can see it by running the same scenario with a jvm 8.

Still searching but we are not alone :)
See https://answers.launchpad.net/ubuntu/+question/239272
See https://community.oracle.com/thread/2382681?tstart=0

I've tested to fetch the certificate and import it in java keystore, not better :
sudo keytool  -importcert -file [mycertificate] -keystore /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/security/cacerts

Perhaps by using another security provider like bouncy castle : http://docs.oracle.com/cd/E19830-01/819-4712/ablsc/index.html

TLS_RSA_WITH_RC4_128_SHA
https://bugs.openjdk.java.net/browse/JDK-8076221

Another possible solution is to use the oracle jdk...
