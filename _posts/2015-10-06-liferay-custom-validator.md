---
layout: post
title: Liferay_custom_validator
categories: []
tags: []
published: True

---

Since 6.2 version you can avoid defining complex javascripts structures to define your own aui validator (http://www.liferaysavvy.com/2014/01/aui-form-validator-in-liferay.html).

You can now execute the same thing with few lines like this:

<aui:input model="<%= User.class %>" name="screenName" max="8">
    <aui:validator name="required" />
    <aui:validator name="custom" errorMessage="Screen name invalid.">
         function (val, fieldNode, ruleValue) {
             return  (/^[0-9]{7}[A-Z]{1}$/.test(val));
         }
    </aui:validator>
</aui:input>

