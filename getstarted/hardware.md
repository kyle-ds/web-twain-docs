---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Hardware
keywords: Dynamic Web TWAIN, Documentation, TWAIN, ICA, SANE, DirectShow, Webcam, MediaDevices Hardware
breadcrumbText: Hardware
description: Dynamic Web TWAIN SDK Documentation Hardware Page
---

# Hardware

`DWT`'s main feature is interacting with imaging devices like scanners and cameras. In this section, we'll look at the supported devices.

- [TWAIN Scanners](#twain-scanners)
- [ICA Scanners](#ica-scanners)
- [SANE Scanners](#sane-scanners)
- [DirectShow Cameras](#directshow-cameras)
- [MediaDevices Cameras](#mediadevices-cameras)

## TWAIN Scanners

![Hardware-Scanners-Cameras-1]({{site.assets}}imgs/Hardware-Scanners-Cameras-1.png)

`TWAIN Scanners` refer to image scanners that have drivers following the TWAIN standard.

### Facts about TWAIN

* TWAIN is an application programming interface (API) and communication protocol that regulate communication between software and digital imaging devices, such as image scanners and digital cameras. 

* TWAIN is supported on Microsoft Windows, Linux, and macOS X. However, based on our experience and the experience of many customers, TWAIN only works well on Windows. On Linux, [SANE](#sane-scanners) is the better and preferred alternative; on macOS, [ICA](#ica-scanners) is the better and preferred alternative.

* TWAIN is actively maintained by the non-profit [TWAIN Working Group](https://www.twain.org/). Members of the group consists of scanner vendors and imaging software vendors, including FUJITSU, Panasonic, Epson, HP, ExactCODE, LEADTOOLS, and of course, Dynamsoft.

* TWAIN is [the most commonly used protocol](https://www.twain.org/why-twain/) for image capturing and processing. Almost all scanners on the market come with a TWAIN driver and are supported by TWAIN applications like `DWT` .

### Is my Scanner TWAIN Compliant?

After you have installed the driver for your scanner, you can refer to the following methods to verify whether your scanner is TWAIN compliant.


* [Recommended & Easiest] Take advantage of our official demo page

  + Open the [demo page](https://demo.dynamsoft.com/dwt/online_demo_scan.aspx) on [Windows]({{site.getstarted}}platform.html#browsers-on-windows)

  > If you haven't installed DWT, a dialog will show up asking you to download and install it.

  + Make sure the scanner driver shows up in the scanner dropdown list

![Hardware-Scanners-Cameras-5]({{site.assets}}imgs/Hardware-Scanners-Cameras-5.png)

  + If the scanner appears in the dropdown, try scanning to make sure it works correctly without any errors. Errors will appear in the message box under the viewer. 

* [Recommended] Use the tool called `Twacker` which is developed by the [TWAIN Working Group](https://www.twain.org/)

  + Download and install

    > In most cases, please dowload the 32-bit version

    - [32-bit](https://download.dynamsoft.com/tool/Twack_32.msi)
    - [64-bit](https://download.dynamsoft.com/tool/Twack_64.msi)

  + Open the program

![Hardware-Scanners-Cameras-6]({{site.assets}}imgs/Hardware-Scanners-Cameras-6.png)

  + Select your device

![Hardware-Scanners-Cameras-7]({{site.assets}}imgs/Hardware-Scanners-Cameras-7.png)

  > If your device is not listed, please check if the driver is installed. Or, try running `Twacker` as admin to see if it shows up.

  + Choose the settings and try scanning

![Hardware-Scanners-Cameras-8]({{site.assets}}imgs/Hardware-Scanners-Cameras-8.png)

  > If scanning is successful without any errors, then your device should be TWAIN compliant. You can also try other commands to see how it works. If your scanner doesn’t work with `TWACKER` , please check your scanner model online and make sure you have installed the (latest) TWAIN driver from its manufacturer.

![Hardware-Scanners-Cameras-9]({{site.assets}}imgs/Hardware-Scanners-Cameras-9.png)

* Refer to the official [twain-certified-drivers](https://resource.twain.org/twain-certified-drivers/). 

> This list is maintained by hardware vendors and may be incomplete. In this case, try the two ways above instead.

### No Scanner to test

If you don't have a TWAIN scanner at hand to test the library. You can download and use a virtual scanner. 

* [32-bit virtual scanner](https://www.dynamsoft.com/download/TWAIN/twainds.win32.installer.2.1.3.msi)
* [64-bit virtual scanner](https://www.dynamsoft.com/download/TWAIN/twainds.win64.installer.2.1.3.msi)

### TWAIN and WIA

`WIA` refers to [Windows Image Acquisition](https://docs.microsoft.com/en-us/windows/win32/wia/-wia-startpage), which is the still image acquisition platform in the Windows family that enables imaging/graphics applications to interact with imaging hardware and standardizes the interaction between different applications and scanners. 

`WIA` devices can be used by `TWAIN` applications like `DWT` through a `TWAIN compatibility layer`. This means `WIA` is not supported natively; therefore, when a device supports both `TWAIN` and `WIA` , `TWAIN` is the better option.

By comparison, `WIA` can only control a very limited set of general capabilities of the devices while `TWAIN` can control all standard and even custom capabilities of the devices. Another thing is that `TWAIN` has three transfer modes (Native, Memory, File), while `WIA` only has two (Memory, File).

## ICA Scanners

![Hardware-Scanners-Cameras-2]({{site.assets}}imgs/Hardware-Scanners-Cameras-2.png)

`ICA Scanners` refer to image scanners that have drivers designed in accordance with the [ImageCaptureCore Framework](https://developer.apple.com/documentation/imagecapturecore).

### Facts about ICA

* ICA is a framework from Apple designed to "Browse for media devices and control them programmatically from your app."

* ICA is supported on macOS X.

### Is my Scanner ICA Compliant?

There are 3 ways to verify whether your scanner is ICA compliant. 

* [Recommended & Easiest] Take advantage of our official demo page

  + Open the [demo page](https://demo.dynamsoft.com/dwt/online_demo_scan.aspx) on [macOS]({{site.getstarted}}platform.html#browsers-on-macos)

  > If you haven't installed DWT, a dialog will show up for you to download and install it.

  + Make sure the scanner driver shows up in the scanner list.

![Hardware-Scanners-Cameras-5]({{site.assets}}imgs/Hardware-Scanners-Cameras-5.png)

  + Try scanning to make sure it works correctly without any errors

* [Recommended] Try the scanner with the ImageCapture app on macOS. 

  + Find the Image Capture application

![Hardware-Scanners-Cameras-12.png]({{site.assets}}imgs/Hardware-Scanners-Cameras-12.png)

  + Open the application

![Hardware-Scanners-Cameras-13.png]({{site.assets}}imgs/Hardware-Scanners-Cameras-13.png)

  + Acquire an image and see how it works

![Hardware-Scanners-Cameras-14.png]({{site.assets}}imgs/Hardware-Scanners-Cameras-14.png)

  For more info, please check out the [official guide](https://support.apple.com/en-ca/guide/image-capture/imgcp1004/mac).

* Check out the [official list](https://support.apple.com/en-us/HT201465) of supported ICA scanners on MacOS. 

## SANE Scanners

![Hardware-Scanners-Cameras-3]({{site.assets}}imgs/Hardware-Scanners-Cameras-3.png)

`SANE Scanners` refer to image scanners that have drivers designed in accordance with the [SANE API](http://www.sane-project.org/).

### Facts about SANE

* SANE stands for "Scanner Access Now Easy" and is an application programming interface (API) that provides standardized access to any raster image scanner hardware.

* SANE is supported on multiple Linux distributions.

* As of version 16.1.1, `DWT` supports SANE v1.0.25.

### Is my Scanner SANE Compliant?

There are 3 ways to verify whether your scanner is SANE compliant.

* [Recommended & Easiest] Take advantage of our official demo page

  + Open the [demo page](https://demo.dynamsoft.com/dwt/online_demo_scan.aspx) on [Linux]({{site.getstarted}}platform.html#browsers-on-linux)

  > If you haven't installed the SDK, a dialog will show up for you to download and install it.

  + Make sure the scanner driver shows up in the scanner list

![Hardware-Scanners-Cameras-5]({{site.assets}}imgs/Hardware-Scanners-Cameras-5.png)

  + Try scanning to make sure it works correctly without any errors

* [Recommended] Try the scanner with the XSane app on Linux. Check out the [official guide](http://www.fifi.org/doc/xsane/html/sane-xsane-doc.html)

> [More info>>]({{site.assets}}docs/Scanning_with_XSane.pdf)

* Check out the [official list](http://www.sane-project.org/sane-backends-1.0.25.html) of supported scanners. 

## DirectShow Cameras

![Hardware-Scanners-Cameras-4]({{site.assets}}imgs/Hardware-Scanners-Cameras-4.png)

`DirectShow Cameras` refer to the cameras which can be accessed via the [Microsoft DirectShow architecture](https://docs.microsoft.com/en-us/windows/win32/directshow/introduction-to-directshow). These cameras are either built into desktops / laptops or connected via USB.

### Is my Camera DirectShow Compliant?

* [Recommended] Take advantage of our official demo page

  + Open the [demo page](https://demo.dynamsoft.com/DWT/Webcam/online_demo_scan_Webcam.aspx) on [Windows]({{site.getstarted}}platform.html#browsers-on-windows)

  > If you haven't installed the SDK, a dialog will show up for you to download and install it.

  + Make sure the camera shows up in the device list

![Hardware-Scanners-Cameras-10]({{site.assets}}imgs/Hardware-Scanners-Cameras-10.png)

  + Try showing the video stream and try capturing a frame to see if it works without any errors

* Try the camera with the [Amcap app](https://tst.dynamsoft.com/public/download/tools/amcap.zip) and see if it works correctly.

## MediaDevices Cameras

`MediaDevices Cameras` refers to the cameras accessible via the [MediaDevices interface](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices). These cameras are either built into desktops/laptops/mobile devices, including phones and tablets, or connected via USB.

> `DirectShow Cameras` and `MediaDevices Cameras` could refer to the same devices which can be accessed either way.

### Is my Camera MediaDevices Compliant?

* [Recommended] Take advantage of our official demo page

  + Open the [demo page](https://demo.dynamsoft.com/Samples/dwt/Pure-JS-Solution/PureJSSolution.html?utm_source=dwtdocs)

  + Make sure the camera shows up in the device list

![Hardware-Scanners-Cameras-11]({{site.assets}}imgs/Hardware-Scanners-Cameras-11.png)

  + Try showing the video stream and capturing a frame to see if it works without any errors

## FAQs

### How to exclude WIA sources in the source list

> Applicable to Windows only

There are two ways to achieve this:

* Set `IfUseTwainDSM` to `true`

``` javascript
DWObject.IfUseTwainDSM = true;
```

* Filter sources before listing them

``` javascript
var sources = DWObject.GetSourceNames();
for (var i = 0; i < sources.length; i++) {
    if (sources[i].toLowerCase().indexOf('epson') != -1) {
        sources.splice(i, 1);
    }
}
```

If you are still having issues with a device after reading the above information. You can.. 

  + Check out [hardware issue]({{site.indepth}}troubleshooting/scanners-hardware.html) troubleshooting page,
  + Or contact [Dynamsoft Support]({{site.about}}getsupport.html)
