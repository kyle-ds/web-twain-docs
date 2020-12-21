---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting Activating The WebTwain Instance Prompt Doesn't Disappear 
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, Activating The WebTwain Instance Prompt Doesn't Disappear 
breadcrumbText: Activating The WebTwain Instance
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Activating The WebTwain Instance Prompt Doesn't Disappear  Page
---

# Handling Errors


## 'Activating the WebTwain instance' prompt doesn't disappear 

* Symptom

We have encountered many a such issue that when running DWT in WASM mode, it doesn't get past the step that says 'Activating the WebTwain instance'. 

![activating-the-WebTwain-instance-1]({{site.assets}}imgs/activating-the-WebTwain-instance-1.png)

* Cause

The cause is that the wasm has been served with an incorrect MIME type in which case the browser won't be processing the wasm after it is downloaded as it doesn't know how to handle such files, therefore it stops dead there. To confirm the issue, open dev tools and switch to network and you'll see something similar to this (note that content-type is wrong, it may not be what you see in this example but it's definitely not application/wasm. 

Notice that there are no more activity after this in network.

![activating-the-WebTwain-instance-2]({{site.assets}}imgs/activating-the-WebTwain-instance-2.png)

If it's right, more wasm files will follow like this:

![activating-the-WebTwain-instance-3]({{site.assets}}imgs/activating-the-WebTwain-instance-3.png)

* Resolution

Make sure the wasm files can be served correctly. Different servers are configured differently. Here are some popular ones:

NGINX: [ `mime.types` ](https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types)
IIS: [ `Web.config` ](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)
Java™ EE web app: [ `web.xml` ](https://docs.oracle.com/cd/E24329_01/web.1211/e21049/web_xml.htm#WBAPP533)
Node.js: [ `npm mime` ](https://www.npmjs.com/package/mime-types)