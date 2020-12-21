---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting XMLHttpRequest Cannot Load XXX
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, XMLHttpRequest Cannot Load XXX
breadcrumbText: XMLHttpRequest Cannot Load
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors XMLHttpRequest Cannot Load XXX
---

# Handling Errors

## XMLHttpRequest cannot load XXX

* Symptom

	You get the error

	``` shell
	XMLHttpRequest cannot load xxxxx. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://xxxxxxx' is therefore not allowed access.
	```

* Cause

	You are uploading or downloading to/from a web server which is in a different domain than your current website and that web server doesn't allow accessing from a different domain.

* Solution

	Try uploading to the same domain or update the server side configuration to allow cross domain requests. If you are using IIS, you can refer to the following configuration.

	``` xml
	<system.webServer>
	    <httpProtocol>
	            <customHeaders>
	            <add name="Access-Control-Allow-Origin" value="*" />
	            <add name="Access-Control-Allow-Methods" value="OPTIONS, POST, GET, PUT" />
	            <add name="Access-Control-Allow-Headers" value="x-requested-with" />
	            <add name="Access-Control-Allow-Credentials" value="true" />
	        </customHeaders>
	    </httpProtocol>
	</system.webServer>
	```

> Note
>  
> After updating the server configuration file, you'll need to restart the server (i.e. IIS).
>  
> If you are downloading a file, you might need to clear the browser cache because a cached file will not be requested again from the server, thus still no 'Access-Control-Allow-Origin' header will be presented.
>  
> If you are using Windows Authentication, you may need to change the default setting of `withCredentials` in the `dynamsoft.webtwain.initiate.js` file. To do that, open the JS file, find `withCredentials:false` and change it to `withCredentials:true` .