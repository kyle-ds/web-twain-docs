---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting Only 24-bit True Color bmp And 8-bit gray-scaled Image Are Supported For JPEG Compression
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, JPEG Compression
breadcrumbText: JPEG Compression
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors JPEG Compression Page
---

# Handling Errors

## Only 24-bit true color bmp and 8-bit gray-scaled image are supported for JPEG compression

* Symptom

When you save or upload an image as a JPEG file, you may receive the error.

* Cause

You are saving a Black&White image as a JPEG file but JPEG standard only allows the compression of grayscale and RGB images.

* Resolution

Make sure the pixel type of the image in the buffer is Gray or RGB. If it is not, you can either save it in another format or convert the image to grayscale using the method [ConvertToGrayScale()]({{site.info}}api/WebTwain_Edit.html#converttograyscale).

``` javascript
if ( /*If save in JPEG*/ ) {

    //Check whether the current image is B&W
    //1 is B&W, 8 is Gray, 24 is RGB
    if (DWObject.GetImageBitDepth(DWObject.CurrentImageIndexInBuffer) == 1)
        //If so, convert the image to Gray
        DWObject.ConvertToGrayScale(DWObject.CurrentImageIndexInBuffer);
    //Save image in JPEG
    DWObject.SaveAsJPEG("DynamicWebTWAIN.jpg", DWObject.CurrentImageIndexInBuffer);

}
```