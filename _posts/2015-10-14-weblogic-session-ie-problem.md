---
layout:
title: weblogic_session_ie_problem
categories: []
tags: []
published: True

---

------------
The problem
------------

I got a portal. In that portal an embedded web application allows to download files.
Under IE or Safari the files can't be downloaded. As far as this is JSF here is the piece of log:
{% highlight sh %}
javax.faces.application.ViewExpiredException: viewId:/decomptes.jsf - La vue «/xxx.jsf» n’a pas pu être restaurée.
    at com.sun.faces.lifecycle.RestoreViewPhase.execute(RestoreViewPhase.java:205)
    at com.sun.faces.lifecycle.Phase.doPhase(Phase.java:101)
{% endhighlight %}

-------------------------------
I already had a similar problem
-------------------------------
I already got session problems with my portal. This was previously due to the cookie path that was the same all around my web applications.
But the problem was that the portal is using session and web application were stateless.
By having the same JSESSIONID cookie name and cookie path set to "/" we were losing sessions. I've fixed it by setting a specific cookie path to my portal "/portal".

-------------------------------------
People with same problems leads me...
-------------------------------------

http://stackoverflow.com/questions/8292449/internet-explorer-sends-the-wrong-cookie-when-the-paths-overlap

The problem is why only on Safari and IE, this is session, so this server oriented!
The fact is the cookie policies and strategies depends on browser. And I've discovered like described in the above link that it was true.
Having my portal with a cookie path "/portal" and let's say a web application with "/portal-my-webapp" was a cause of a disaster. IE or Safari are propagating cookies because this is not ended with a slash! That's why having the common root "/portal" was buggy and it leads to overwrite my webapps cookies (so losing sessions).

But why in hell was it happening now? It was not the first time I've deployed this Liferay portal!
This was due to previously having used Tomcat or JBoss. They have a default parameter called trailing slash that was always added, so fixing those browsers bugs.
But under Weblogic 12c this is not managed automatically.

----------
Conclusion
----------

Thank you Weblogic, thanks to you I have to think a little bit and now I understand more IE/Safari logic for session handling ;)
