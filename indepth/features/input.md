---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Features - Input
keywords: Dynamic Web TWAIN, Documentation, Input
breadcrumbText: Input
description: Dynamic Web TWAIN SDK Documentation Input Page
---

# Input

This section introduces different ways to get data into the `DWT` buffer.

## Scan

### Scan From a Local Scanner

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and only when `DWT` runs in [service mode]({{site.indepth}}features/initialize.html#service-mode)

A local scanner refers to a scanner that is plugged in the same desktop via USB or is available on the local network and is accessible on the local desktop. The latter is generally known as a network scanner. A network scanner is connected to the LAN itself (cable or WI-FI) and is assigned a static IP. The scanner driver from the device vendor then configures the IP to connect to the scanner.

> As far as `DWT` is concerned, a network scanner is just like a local scanner because its driver has taken care of the network connection behind the scene.

### Scan From a Remote Scanner

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices) platforms.

A remote scanner refers to a scanner that is..

* Not connected to the initiating device
* Connected and accessible on a `Windows` desktop on LAN (USB or network) where `DWT` must be installed

For more information, check out [how to enable remote scan](#how-to-enable-remote-scan).

<!--

### Scan from a TWAIN-Direct scanner

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices).

A TWAIN-Direct scanner refers to a device that supports the next generation of the TWAIN protocal called [ `TWAIN-Direct` ](https://www.twaindirect.org/).

For more information, check [How to use a TWAIN-Direct scanner](#how-to-use-a-twain-direct-scanner).
-->

### FAQs

#### Q: How do you configure the scan?

**A**: `DWT` provides two ways to set up a scan operation.

1. Change one setting at a time. Below are a few APIs, for example
  + [PageSize]({{site.info}}api/WebTwain_Acquire.html#pagesize) 
  + [PixelType]({{site.info}}api/WebTwain_Acquire.html#pixeltype)
  + [Resolution]({{site.info}}api/WebTwain_Acquire.html#resolution) 
  + [SourceCount]({{site.info}}api/WebTwain_Acquire.html#sourcecount)
2. Change all settings at once. Use one of the two APIs below to achieve this.
  + [AcquireImage()]({{site.info}}api/WebTwain_Acquire.html#acquireimage)
  + [startScan()]({{site.info}}api/WebTwain_Acquire.html#startscan)

#### Q: How many images can be scanned?

**A**: Check out [Buffer Management]({{site.indepth}}features/buffer.html#memory-limits-and-disk-caching)

#### Q: How do you use Custom DataSource Data?

> This feature is only available for [TWAIN scanners]({{site.getstarted}}hardware.html#twain-scanners).

**A**: Custom DataSource Data (CDD) is a feature provided by TWAIN and implemented by TWAIN sources (drivers). The idea is to save all TWAIN-related configurations in a file or a base64 string and use it later to restore the same configurations on the same device or a different device of the same model. This feature can be handy in cases like sharing the same configurations across multiple devices, or presetting a device for scanning. `DWT` provides two pairs of methods to enable this feature, which are

* [ `GetCustomDSData()` ]({{site.info}}api/WebTwain_Acquire.html#getcustomdsdata) , [ `SetCustomDSData()` ]({{site.info}}api/WebTwain_Acquire.html#setcustomdsdata)
* [ `GetCustomDSDataEx()` ]({{site.info}}api/WebTwain_Acquire.html#getcustomdsdataex) , [ `SetCustomDSDataEx()` ]({{site.info}}api/WebTwain_Acquire.html#setcustomdsdataex)

The first pair saves or loads the data from a file, and the second from a base64 string.

The following shows how to use the second pair in JavaScript.

##### Save the data

``` javascript
  var cDD = "";
  DWObject.SelectSource(function() {
      DWObject.OpenSource();
      DWObject.AcquireImage(function() {
          cDD = DWObject.GetCustomDSDataEx();
      }, function(code, error) {
          console.log(error);
      });
  }, function(code, error) {
      console.log(error);
  });
```

##### Use the data

``` javascript
  DWObject.SelectSource(function() {
      DWObject.IfShowUI = false;
      DWObject.OpenSource();
      DWObject.SetCustomDSDataEx(cDD);
      DWObject.AcquireImage(function() {
          console.log('Success');
      }, function(code, error) {
          console.log(error);
      });
  }, function(code, error) {
      console.log(error);
  });
```

#### Q: How do you use Capability Negotiation?

> This feature is only available for [TWAIN scanners]({{site.getstarted}}hardware.html#twain-scanners)

**A**: Capability Negotiation is the way a TWAIN application communicates with a TWAIN source. This is how `DWT` communicates with a scanner. The process looks something like this:

* [DWT] Are you capable of ***?
* [Scanner] Yes, and here is what I can do...
* [DWT] Great, here is what I want done...
* [Scanner] Consider it done

`DWT` provides two methods, `getCapabilities()` and `setCapabilities()`, for negotiation. The following shows how to ask for supported page sizes and set it to A4 using Capability Negotiation.

##### Ask for supported sizes

``` javascript
DWObject.getCapabilities(function(result) {
    for (var i = 0; i < result.length; i++) {
        if (result[i].capability.value === Dynamsoft.EnumDWT_Cap.ICAP_SUPPORTEDSIZES)
            sizes = result[i].values;
    }
    console.log(sizes);
}, function(error) {
    console.log(error);
});
```

##### Set page size to A4

``` javascript
DWObject.setCapabilities({
        exception: "ignore",
        capabilities: [{
            capability: Dynamsoft.EnumDWT_Cap.ICAP_SUPPORTEDSIZES,
            curValue: 1, // 1 means 'A4' in our case
            exception: "fail"
        }]
    },
    function(result) {
        console.log(result)
    },
    function(error) {
        console.log(error);
    }
);
```

#### Q: How do you use a custom capability?

**A**: The TWAIN specification defines more than 150 standard capabilities for TWAIN applications and sources to choose from. However, some scanner vendors provide advanced and model-specific capabilities which are not included in the specification. We call them custom capabilities. The following steps show how to use them:

1. Install the [TWAIN Sample App](http://www.dynamsoft.com/download/support/twainapp.win32.installer.msi).

2. Use the TWAIN Sample App to open the source and then check what the hexadecimal value of the custom capability is.

![Indepth-input-1]({{site.assets}}imgs/Indepth-input-1.png)

3. Double click and check the available values.

![Indepth-input-2]({{site.assets}}imgs/Indepth-input-2.png)

4. Use this custom capability.

``` javascript
DWObject.SelectSource(function() {
        DWObject.OpenSource();
        DWObject.setCapabilities({
                exception: "ignore",
                capabilities: [{
                    capability: 0xA03D,
                    curValue: 3,
                    exception: "fail",
                }]
            },
            function(capabilities) {
                console.log(capabilities);
            },
            function(error) {
                console.error(error);
            });
    },
    function(code, error) {
        console.log(error);
    }
);
```

## Capture

### Use [DirectShow Cameras]({{site.getstarted}}hardware.html#directshow-cameras)

The following code snippet shows how to use a camera through `DirectShow`.
  

``` javascript
function PlayVideo(bShow) {
    if (DWObject) {
        DWObject.Addon.Webcam.StopVideo();
        DWObject.Addon.Webcam.SelectSource("CAMERA-NAME");
        DWObject.Addon.Webcam.PlayVideo(DWObject, 80, function() {});
    }
}

function CaptureImage() {
    if (DWObject) {
        DWObject.Addon.Webcam.SelectSource("CAMERA-NAME");
        var funCaptureImage = function() {
            setTimeout(function() {
                DWObject.Addon.Webcam.StopVideo();
            }, 50);
        };
        DWObject.Addon.Webcam.CaptureImage(funCaptureImage, funCaptureImage);
    }
}
```

### Use [MediaDevices Cameras]({{site.getstarted}}hardware.html#mediadevices-cameras)

The following code snippet shows how to use a camera through `MediaDevices`.

``` javascript
var videoPlaying = false;

function PlayVideo(bShow) {
    if (videoPlaying) return;
    if (DWObject) {
        DWObject.Addon.Camera.stop();
        videoPlaying = false;
        // DEVICE-ID must be correct
        // e.g.: "592bbc7c0f951657d8dc6dc3af8bdd76cde89b78184a8475f70eb012a4040a54"
        DWObject.Addon.Camera.selectSource("DEVICE-ID");
        DWObject.Addon.Camera.play()
            .then(function() {
                videoPlaying = true;
            });
    }
}

function CaptureImage() {
    if (DWObject) {
        PlayVideo();
        var startCapture = function() {
            setTimeout(function() {
                if (videoPlaying) {
                    DWObject.Addon.Camera.capture().then(function(blob) {
                        DWObject.Addon.Camera.stop();
                        videoPlaying = false;
                    });
                } else {
                    startCapture();
                }
            }, 50);
        };
        startCapture();
    }
}
```

## Load

Load in this context means to open files which are accessible on the file system. These files can reside on the local disk or shared on the network.

> As a lightweight library, `DWT` only supports the following file types: BMP, JPG, TIF, PNG, and PDF. However, not all files of these types can be loaded correctly. Learn more [here]({{site.getstarted}}Filetype.html). If you come across a file that is of one of the supported file types but fails to load, please contact [Dynamsoft Support]({{site.about}}getsupport.html).

### [Recommended] Show the `Open File` dialog and select files to load.

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices) platforms. 

The `Open File` dialog is only displayed on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices). On mobile browsers, users are presented with the option to take a picture, use an existing image on the device, or open an existing file stored on the device. 

``` javascript
var onSuccess = function() {
    console.log("Loaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.IfShowFileDialog = true;
// PDF Rasterizer Addon is used here to ensure PDF support
DWObject.Addon.PDF.SetResolution(200);
DWObject.Addon.PDF.SetConvertMode(Dynamsoft.EnumDWT_ConvertMode.CM_RENDERALL);
DWObject.LoadImageEx("", Dynamsoft.EnumDWT_ImageType.IT_ALL, onSuccess, onFailure);
```

### Open an existing file using its absolute path

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and only when `DWT` runs in [service mode]({{site.indepth}}features/initialize.html#service-mode). 

``` javascript
var onSuccess = function() {
    console.log("Loaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.IfShowFileDialog = false;
// PDF Addon is used here to ensure PDF support
DWObject.Addon.PDF.SetResolution(200);
DWObject.Addon.PDF.SetConvertMode(Dynamsoft.EnumDWT_ConvertMode.CM_RENDERALL);
/* "YOUR-FILE-PATH" - example path
 * Windows: 
 *   Local: "D:\\Files\\sample.pdf"
 *   LAN: "\\\\192.168.1.45\\sme\\sample.tif"
 * macOS: "/Applications/Images/sample.pdf"
 * Linux: "/home/userA/Files/sample.pdf"
 */
DWObject.LoadImage("YOUR-FILE-PATH", onSuccess, onFailure);
```

### Drag and drop files onto the viewer area of a `WebTwain` instance

> Only supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) platform.

### Download

> `Download` is another type of `Load`. The only difference between a `Download` with what's written above is that the file to load needs to be transferred to the local device via the network first. `DWT` takes care of the whole process and supports both `HTTP` and `FTP`.

#### `HTTP` or `HTTPS`

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices) platforms. For this option, a URL is used to fetch the file. The URL either specifies the path of the file itself or points to a server-side script that eventually returns a file. Check out the code snippets below demonstrating both scenarios.

##### The URL specifies a file

``` javascript
/* The sample file path is: 
 * "http://localhost:300/files/sample.tif"
 */
var onSuccess = function() {
    console.log("Downloaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.HTTPPort = 300;
DWObject.HTTPDownload("localhost", "/files/sample.tif", onSuccess, onFailure);
```

##### The URL points to a server-side script

> The method `HTTPDownloadEx` is used because the file type needs to be specified.

JavaScript

``` javascript
/* The sample file path is: 
 * "http://localhost:300/files/sample.tif"
 */
var onSuccess = function() {
    console.log("Downloaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.HTTPPort = 300;
DWObject.HTTPDownloadEx("localhost", "/getFile.aspx", Dynamsoft.EnumDWT_ImageType.IT_TIF, onSuccess, onFailure);
```

Server-side script

> The server-side script can be written in any language and in any logic as long as it returns a file.

``` csharp
<%@ Page Language="C#"%>
<%
try
{
    String fileName = "sample.tif";
    String filePath = Server.MapPath(".") + "\\files\\" + fileName;
    System.IO.FileInfo fileInfo = new System.IO.FileInfo(filePath);
    Response.ClearContent();
    Response.ClearHeaders();
    Response.Clear();
    Response.Buffer = true;
    String fileNameEncode;
    fileNameEncode = HttpUtility.UrlEncode(fileName, System.Text.Encoding.UTF8);
    fileNameEncode = fileNameEncode.Replace("+", "%20");
    String appendedheader = "attachment;filename=" + fileNameEncode;
    Response.AppendHeader("Content-Disposition", appendedheader);
    Response.WriteFile(fileInfo.FullName);
    }
catch (Exception)
{	}
%>
```

#### `FTP`

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) platform.

The following code shows how to download a file from FTP.

``` javascript
/* The sample file path is: 
 * "ftp://192.168.8.20/files/sample.pdf"
 */
var onSuccess = function() {
    console.log("Downloaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.FTPPort = 21;
DWObject.FTPUserName = "FTPUser";
DWObject.FTPPassword = "SomePassword";
DWObject.FTPDownloadEx("192.168.8.20", "/files/sample.pdf", Dynamsoft.EnumDWT_ImageType.IT_PDF, onSuccess, onFailure);
```

### Load files in binary or base64 string format 

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices) platforms.

`DWT` is capable of reading files in binary or base64 string format.

``` javascript
var onSuccess = function() {
    console.log("Loaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
/**
 * The following function loads a binary/blob. 
 * The method ConvertToBlob() is used to create
 * the Blob as an example but the actual Blob can 
 * come from anywhere.
 */
function loadFileFromBinary() {
    if (DWObject) {
        DWObject.ConvertToBlob(
            [0],
            Dynamsoft.EnumDWT_ImageType.IT_PDF,
            function(result) {
                DWObject.LoadImageFromBinary(
                    result, onSuccess, onFailure);
            }, onFailure);
    }
}
/**
 * The following function loads a base64 string. 
 * The method ConvertToBase64() is used to create
 * the string as an example but the string can 
 * come from anywhere.
 * NOTE: the prefix such as "data:image/png;base64,"
 * should NOT be included in the data to load.
 */
function loadFileFromBase64() {
    if (DWObject) {
        DWObject.ConvertToBase64(
            [0],
            Dynamsoft.EnumDWT_ImageType.IT_PDF,
            function(result) {
                DWObject.LoadImageFromBase64Binary(
                    result.getData(0, result.getLength()),
                    Dynamsoft.EnumDWT_ImageType.IT_PDF,
                    onSuccess, onFailure);
            }, onFailure);
    }
}
```

### Load files from the system clipboard

> Supported on [desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and only when `DWT` runs in [service mode]({{site.indepth}}features/initialize.html#service-mode).

``` javascript
DWObject.LoadDibFromClipboard()
```

## Other Topics

### Select a scanner by its name

Use the method `SelectSourceByIndex()` to select a scanner by its index in the source list. In some cases, you may want to select a source by its name as shown in the example below.

``` javascript
var sources = DWObject.GetSourceNames();
sources.find(function(name, index) {
    //"EPSON DS-530" is the name of the scanner
    if (name === "EPSON DS-530")
        DWObject.SelectSourceByIndex(index);
})
```

### How to enable remote scan

#### On Windows desktop where the scanner is physically connected

1. Install `Dynamsoft Service`
2. Configure the Service by adding the following line to the file `DSConfiguration.ini` 

``` 
Server=192.168.8.221
```
  > We are assuminge the IP of this desktop is `192.168.8.221`

3. Find the service `Dynamsoft Service` in Windows services list and restart it.

#### In your application

4. Create a WebTwain instance to connect to that service

> Learn more [here]({{site.indepth}}features/initialize.html#dynamsoftwebtwainenvcreatedwtobject)

``` javascript
Dynamsoft.WebTwainEnv.CreateDWTObject(
    "dwtcontrolContainer",
    "192.168.8.221", 18622, 18623,
    function(dwtObject) {
        DWObject = dwtObject;
    },
    function(errorString) {
        console.log(errorString);
    }
);
```

1. Use this WebTwain instance, `DWObject`, to scan documents from the scanner connected to the desktop (192.168.8.221)

<!--

### How to use a TWAIN-Direct scanner

-->

### How to scan only a selected region

#### Set `PageSize`

``` javascript
DWObject.SelectSource(function() {
    DWObject.OpenSource();
    DWObject.IfShowUI = false;
    DWObject.PageSize = Dynamsoft.EnumDWT_CapSupportedSizes.TWSS_USLEGAL;
    DWObject.AcquireImage();
});
```

#### Set a layout with `SetImageLayout`

``` javascript
DWObject.SelectSource(function() {
    DWObject.OpenSource();
    DWObject.IfShowUI = false;
    DWObject.Unit = EnumDWT_UnitType.TWUN_INCHES;
    DWObject.SetImageLayout(0, 0, 5, 5);
    DWObject.AcquireImage();
});
```
