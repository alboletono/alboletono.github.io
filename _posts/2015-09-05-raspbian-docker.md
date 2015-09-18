---
layout: link
title: Raspbian_Docker
categories: []
tags: []
published: True
link: http://www.le-libriste.fr/2015/01/installer-docker-sur-un-raspberry-pi-tournant-sous-raspbian/
---

Heureux acquéreur depuis peu d'un raspberry Pi 2, j'ai trouvé ce lien pour mettre en place facilement docker sous Raspian.
On doit donc juste suivre les instructions du site original : https://github.com/debian-pi/raspbian-ua-netinst.

Voici les commandes jouées :

{% highlight sh %}
wget https://github.com/debian-pi/raspbian-ua-netinst/releases/download/v1.0.7/raspbian-ua-netinst-v1.0.7.img.xz
xzcat raspbian-ua-netinst-v1.0.5.img.xz > /dev/sdX
{% endhighlight %}

Plusieurs choses :
* J'ai choisi d'utiliser une Raspbian car c'est à ce que j'ai lu un des OS les plus optimisés pour la Raspberry. En effet, installer directement une Debian est possible mais le site même de Debian avertit de certains problèmes de stabilités hardwares (cf https://wiki.debian.org/RaspberryPi).
* Je souhaite tout faire à partir de docker, je resterai donc sur un système Raspbian basique et n'exposerai ensuite que des debians "dockerisées".

Tout ça c'est de la théorie, nous verrons donc tout ça dans la pratique très bientôt.
