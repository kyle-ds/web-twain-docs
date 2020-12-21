---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting A Connection With The Server Could Not Be Established
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, Connection Couldn't Be Established
breadcrumbText: Connection Couldn't Be Established
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors Connection Couldn't Be Established Page
---

# Handling Errors

## A connection with the server could not be established

* Symptom

When you upload images to your web server, you may receive the error message.

* Cause

The problem may occur when a connection with the server is not available.

* Resolution
  + Check if the HTTP port you set in your code coincides with the port number you set on your web server. You can use the [HTTPPort]({{site.info}}api/WebTwain_IO.html#httpport) property to set the port number.
  + Make sure the address of the server is available. To check this, you can ping the address from a client machine.

> Note:
> Both the machine name and the IP address of the server can be used for the HTTPUpload method.