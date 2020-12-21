---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting HTTP Request Error
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, HTTP Request Error
breadcrumbText: HTTP Request Error
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors HTTP Request Error Page
---

# Handling Errors

## HTTP request error

* Symptom

When you upload images via HTTP Put, you may get this error.

* Cause
  + The problem may occur if the write permission is not provided on the server.
  + If you use Tomcat, because the value of the `readonly` property is `false` by default, the HTTP Put operation is not allowed.

* Solution
  + Check the write permission at the server.

    - Start Internet Information Services (IIS).
    - Click Web Sites.
    - Right-click the specified work folder, select Properties.
    - Select the Write option at the Directory tab.

  + If you are using Tomcat, the `doPut()` will check to see if the `readonly` property has been changed to `false`. If it has not, the HTTP Put operation is not allowed. Please go to {Tomcat installation directory} -> conf -> web.xml, find the default servlet configuration (org.apache.catalina.servlets. DefaultServlet) and change the `readonly` property to `true` .

``` xml
<init-param>
    <param-name>readonly</param-name>
    <param-value>false</param-value>
</init-param>
```