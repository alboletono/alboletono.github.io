---
layout: post
title: centos_commands
categories: []
tags: []
published: True

---

CentOS 7

To start the network manager:
chkconfig NetworkManager on
service NetworkManager start

By default my enp0s3 was not up:
ifup enp0s3

To reference a new service via a script to call
chkconfig --add newscript

yum search [package]
rpm -ql [package]


