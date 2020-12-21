---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Debug
keywords: Dynamic Web TWAIN, Documentation, Debug
breadcrumbText: Debug
description: Dynamic Web TWAIN SDK Documentation Debug Page
---

# Debugging

## Enable and Collect Verbose Logs

Here is how

* Remove any old log files from `C:\Windows\SysWOW64\Dynamsoft\DynamsoftServicex64_16\log`
* Set [ `LogLevel` ]({{site.info}}api/WebTwain_Util.html#loglevel) to 1 in your code. This property should be set as soon as the `WebTwain` instance is created. For example, in the event `Dynamsoft_OnReady`

``` javascript
function Dynamsoft_OnReady() {
    DWObject = Dynamsoft.WebTwainEnv.GetWebTwain('dwtcontrolContainer');
    DWObject.LogLevel = 1;
}
```

> NOTE
>  
> Changing the property will affect all clients. To collect logs for only one client machine, just add the line `LogLevel=14` to `DSConfiguration.ini` on that specific machine. Check out more [here]({{site.indepth}}deployment/service.html#q-how-to-configure-the-service)

* Reproduce the issue

* Zip the log files in `C:\Windows\SysWOW64\Dynamsoft\DynamsoftServicex64_16\log` and share with [Dynamsoft Support Team]({{site.about}}getsupport.html) via email.

On macOS, the log files are in `Go > Applications > Dynamsoft > DynamsoftServicex64_16 > {installed version No.} > log`

On Linux, the log files are in `/opt/dynamsoft/DynamsoftServicex64_16/log`

## Collect the Dump Files

In the case that the Dynamsoft Service crashes, the dump files can be found in the following location

Windows: `C:\Windows\SysWOW64\Dynamsoft\DynamsoftServicex64_16\dump` .
macOS: `Go > Applications > Dynamsoft > DynamsoftServicex64_16 > {installed version No.} > dump` .
Linux: `/opt/dynamsoft/DynamsoftServicex64_16/dump` .

Afterwards, please send the dump files to [Dynamsoft Support Team]({{site.about}}getsupport.html) and describe the issue to get assistance.

## How to Read Log

### Q: What are these log files for?

**A**:

* dss.log --> For Dynamsoft Service
* nw.log --> Details about the network traffic
* wts.log --> For the client part of Dynamic Web TWAIN HTML5 edition
* wtss.log --> For the server part of Dynamic Web TWAIN HTML5 edition

### Q: What info do we see if Dynamic Web TWAIN SDK is not doing anything?

**A**:

There is a regular polling going on every 30 seconds, in the log, it looks like this

Client-side:

``` 
[Process:  1716 Thread: 17652] [05/23/2018 17:43:45.075] [Debug-0]: CClientProxy:: Send begin task=DefaultSourceName seq=18975 status=8 event=11
[Process:  1716 Thread: 17652] [05/23/2018 17:43:45.090] [Debug-0]: CClientProxy:: Send end 0
[Process:  1716 Thread: 17652] [05/23/2018 17:44:15.150] [Debug-0]: CClientProxy:: Send begin task=DefaultSourceName seq=18976 status=8 event=11
[Process:  1716 Thread: 17652] [05/23/2018 17:44:15.156] [Debug-0]: CClientProxy:: Send end 0
```

Server-side:

``` 
[Process:  5364 Thread:  7536] [05/23/2018 18:01:20.930] [Debug-0]: CTwainServer::receive1 task=DefaultSourceName seq=18478 status=8 event=11
```

### Q: What does a command to the service look like?

**A**: It looks like the following with "id" used to identify which client sent the command and "method" being the action that is being carried out

``` 
cmd = [{
"id" : "467653534", 
"method" : "GetImageByIndex", 
"parameter" : [ 0, 581, 511 ]
}].
```

### Q: What basic information can we get from the log?

**A**: 

* The Operating system

``` 
Windows info: 6.2.9200 Pack: 0.0 Other: PID=2 Type=1 Mask=256
```

* The version of Dynamsoft Web TWAIN (wts.log)

``` 
Activex Version info:32c0048, Dynamic Web TWAIN 14.0 Trial, 14, 0, 0, 0618, x64:0
```

* The version of Dynamosft Service (dss.log)

``` 
Current version info: Dynamsoft Service 1, 4, 0, 0618.
```

* The current LogLevel

``` 
Log Level = 14, 0.
```

* Websocket listening ports

``` 
[Debug-0]: dwt_command, Websocket connection initialized.
[Info-0]: Create websocket context succeed at default 127.0.0.1:18625, use_ssl = false!
[Info-0]: Start websocket service succeed. port = [18625], use_ssl = false.
[Process: 16784 Thread: 15400] [05/23/2018 17:56:44.554] [Info-0]: Websocket Listening starts at port = 18625, use_ssl = false
[Debug-0]: Get the port number and try creating websocket listening.
[Debug-0]: dwt_command, Websocket connection initialized.
[Info-0]: Create websocket context succeed at default 127.0.0.1:18626, use_ssl = true!
[Info-0]: Add https service succeed! Succeed port = 18626, use_ssl = true.
[Process: 16784 Thread: 10740] [05/23/2018 17:56:46.794] [Info-0]: Websocket Listening starts at port = 18626, use_ssl = true
[Debug-0]: Get http service parameter
[Debug-0]: Get the port number and try creating websocket listening.
[Info-0]: Add http service succeed! Succeed port = 18622, use_ssl = false.
[Debug-0]: dwt_command, Websocket connection initialized.
[Info-0]: Create websocket context succeed at default 127.0.0.1:18622, use_ssl = false!
[Info-0]: Start websocket service succeed. port = [18622], use_ssl = false.
[Process: 16784 Thread:  9508] [05/23/2018 17:56:48.071] [Info-0]: Websocket Listening starts at port = 18622, use_ssl = false
```

* Requesting origin

``` 
origin:http://127.0.0.1:100
```

* Sequence in which commands are being called

* How a command worked

``` 
result json = [{
    "description" : "User cancelled the operation.",
    "exception" : -1032,
    "id" : "667465648",
    "method" : "SelectSource",
    "result" : [ false ],
    "cmdId" : ""
}].
```

## WebSocket Connection Issue

`DWT` uses WebSocket connection to communicate with the Dynamsoft Service. Each `WebTwain` instance creates its own Websocket connection. That means if you have multiple `WebTwain` instances, your browser will be maintaining multiple WebSocket connections. At the same time, if you are not proactively closing a connection, then the connection may take some time to close even after you have closed the scan page.

The browser would be tasked with maintaining multiple Websocket connections at some point and not all browsers are designed to handle that. While modern browsers like Chrome, Firefox, etc. can handle tens or even more than a hundred WebSocket connections, IE can handle just 6 by default. Therefore, you may be surprised to find that IE reports the Dynamsoft Service is not installed even when you were just using it! And that report is due to the failure to create a 7th WebsSocket connection at that point.

Though it's not ideal, IE does provide a solution which is to configure the WebSocket connection limit in the Local Group Policy Editor as shown below

* Press the Windows Key + R key to open the Run dialog
* Type `gpedit.msc` and press Enter to open the Local Group Policy Editor
* Navigate to `Administrative Templates` > `Windows Components` > `Internet Explorer` > `Security Features` > `AJAX`
* Double click in the corresponding feature "Maximum number of connections per server" to enable the feature and change the default number to a larger number
