---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting Request Header Field dwt-md5 Is Not Allowed By Access-Control-Allow-Headers In Preflight Response
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, dwt-md5 Is Not Allowed
breadcrumbText: dwt-md5 Is Not Allowed
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors dwt-md5 Is Not Allowed Page
---

# Handling Errors

## Request header field dwt-md5 is not allowed by Access-Control-Allow-Headers in preflight response

* Symptom

	When you fail to upload images, you may get this error

* Cause

	`dwt-md5` is a default built-in header in `DWT` . It is used for each uploading process to test the integrity of data. Since this is not a standard header, the browser will send an OPTIONS preflight request before the original request is sent to verify that this header is allowed. If not, the browser will return the above error.

* Solution

	Update your server-side configuration file as per your environment. If you are using IIS, you can refer to the following configuration.

	``` xml
	<system.webServer>
	    <httpProtocol>
	        <customHeaders>
	            <add name="Access-Control-Allow-Origin" value="*" />
	            <add name="Access-Control-Allow-Methods" value="OPTIONS, POST, GET, PUT" />
	            <add name="Access-Control-Allow-Headers" value="x-requested-with, dwt-md5" />
	            <add name="Access-Control-Allow-Credentials" value="true" />
	        </customHeaders>
	    </httpProtocol>
	</system.webServer>
	```

> Note
>  
> After updating the server configuration file, you'll need to restart the server (i.e. IIS).

Check out more info [here](https://fetch.spec.whatwg.org/#http-cors-protocol)