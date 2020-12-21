---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting HTTP Process Error
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, HTTP Process Error
breadcrumbText: HTTP Process Error
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors HTTP Process Error Page
---


# Handling Errors

## HTTP process error

* Symptom

When you upload images using any of the HTTPUploadThroughPost*** methods, you may receive the error.

* Cause
  + The write permission is not granted to the specified directory on the web server.
  + The action page is incorrect or returns something from the web server.
  + The port specified for uploading is the incorrect one.
  + The size of the images you are trying to upload is beyond the maximum allowed size set by the server.

* Solution
  + Make sure the users who are uploading have permission to write images to the specified directory on the web server. (For example, give "Write" permission to the Authenticated Users.)
  + Check the response string returned from the HTTP server to figure out the cause of the process error. You can get this string by using the [HTTPPostResponseString]({{site.info}}api/WebTwain_IO.html#httppostresponsestring) property.
  + Set the port to the correct one using [HTTPPort]({{site.info}}api/WebTwain_IO.html#httpport). We recommend you get the Port and Server values this way:
  
	``` javascript
		var strHTTPServer = location.hostname;
		DWObject.HTTPPort = location.port == "" ? 80 : location.port;
	```
	+ If you have set [IfSSL]({{site.info}}api/WebTwain_IO.html#ifssl) to true, you must set a secure port for the HTTPPort property. For example, 

	``` javascript
	DWObject.IfSSL = true;
	DWObject.HTTPPort = 443;
	```
> For example: If the URL for the scan page is "http://localhost:3253/....", you should set the port to 3253.

* Checking the server-side configuration is also useful in this scenario
	+ Please reset the maximum transferable data size. If you are using `ASP.NET` , you can change the value in the following line in the `Web.Config` file.

		``` xml
		<httpRuntime maxRequestLength="1000000"/> // In kilobytes
		```

		This line may also be required

		``` xml
		<requestLimits maxAllowedContentLength="300000000" /> // In bytes
		```

		The following is an example config file

		``` xml
		<?xml version="1.0" encoding="UTF-8"?>
		<configuration>
		    <system.web>
		        <httpRuntime executionTimeout="3000"  maxRequestLength="102400"/>
		        <compilation debug="true" />
		    </system.web>
		    <system.webServer>
		        <security>
		            <requestFiltering>
		                <requestLimits maxAllowedContentLength="300000000" />
		            </requestFiltering>
		        </security>
		    </system.webServer>
		</configuration>
		```

		If you are using `PHP` , you can change the value in the following line in the `php.ini` file:

		``` shell
		upload_max_filesize = 2M
		```