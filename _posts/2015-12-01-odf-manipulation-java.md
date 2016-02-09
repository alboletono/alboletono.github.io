---
layout: post
title: Manipulation of ODF format in java
categories: []
tags: []
published: True

---

There are several java api to to that.
I've tested three:
* UNO is too complex to use and soffice is to be installed to work
* JOpenDocument seems interesting but documentation is very basic. This is obviously to sell their support.
* Odf toolkit seems to be just what we need: basic functionalities and good documentation:
  * http://incubator.apache.org/odftoolkit/simple/document/cookbook/index.html


With ODF toolkit, I just have to provide this dependency in my pom and I can run the examples without any effort!

{% highlight java %}
<dependency>
    <groupId>org.apache.odftoolkit</groupId>
    <artifactId>simple-odf</artifactId>
    <version>0.8.1-incubating</version>
</dependency>
{% endhighlight %}
