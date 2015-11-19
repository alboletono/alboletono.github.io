---
layout: link
title: importing_wordpress_to_jekyll
categories: []
tags: []
published: True
link: http://import.jekyllrb.com
---

{% highlight sh %}
sudo -s
gem install jekyll-import
gem install hpricot
gem install open_uri_redirections
ruby -rubygems -e 'require "jekyll-import";
    JekyllImport::Importers::WordpressDotCom.run({
      "source" => "wordpress.xml",
      "no_fetch_images" => false,
      "assets_folder" => "assets"
    })'
{% endhighlight %}

