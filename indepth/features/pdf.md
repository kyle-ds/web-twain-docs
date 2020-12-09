---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Features - Handle PDF
keywords: Dynamic Web TWAIN, Documentation, Handle PDF
breadcrumbText: Handle PDF
description: Dynamic Web TWAIN SDK Documentation Handle PDF Page
---

# PDF Handling 

PDFs are widely used in many and various industries, and presently are the only non-image file type that `DWT` supports. In this next section, we will address all the input and output operations that allow the user to properly handle PDF files.

## Environment

* [Desktop]({{site.getstarted}}platform.html#browsers-on-desktop-devices) and [Mobile]({{site.getstarted}}platform.html#browsers-on-mobile-devices).

* [Service mode]({{site.indepth}}features/initialize.html#service-mode) and [WASM mode]({{site.indepth}}features/initialize.html#wasm-mode).

## Including the PDF addon 

To include the PDF addon, simply add a reference to the corresponding JavaScript file, included in the [resources folder]({{site.about}}faqs.html#what-are-the-resources-files).

> If you are using the [dwt package](https://www.npmjs.com/package/dwt), the barcode reader is already included in the main JavaScript file ( `dynamsoft.webtwain.min.js` or `dynamsoft.webtwain.min.mjs` ) which means you can skip this step.

``` html
<script src="dynamsoft.webtwain.addon.pdf.js"></script>
```

## Input

When loading in a PDF file, `DWT` tries to extract images from that file, which is why the SDK can handle image-based PDF documents by default. However, most existing PDF files contain much more than just images. In this case, we need to make use of the PDF Rasterizer (`PDFR` for short), the main component of the PDF addon.

> How PDFR works: As the name suggests, `PDFR` rasterizes a PDF file page by page much like a scanner. You set a resolution and you get the resulting images in that resolution after the rasterization. 

The following code shows the basic usage

``` javascript
var onSuccess = function() {
    console.log("Loaded a file successfully!");
};
var onFailure = function(errorCode, errorString) {
    console.log(errorString);
};
DWObject.IfShowFileDialog = true;
// PDF Addon is used here to ensure PDF support
DWObject.Addon.PDF.SetResolution(200);
DWObject.Addon.PDF.SetConvertMode(Dynamsoft.EnumDWT_ConvertMode.CM_RENDERALL);
DWObject.LoadImageEx("", Dynamsoft.EnumDWT_ImageType.IT_ALL, onSuccess, onFailure);
```

The method [ `SetConvertMode()` ]({{site.info}}api/Addon_PDF.html#setconvertmode) decides how `PDFR` works and [ `SetResolution()` ]({{site.info}}api/Addon_PDF.html#setresolution) specifies the resolution. These two methods configure `PDFR` to detect and, if necessary, rasterize any PDF file that comes thereafter.

### Questions

#### Q: When do I need to use PDF Rasterizer?

A: `PDFR` is only required for text-based PDFs, to find out whether a file is text-based. Use the method [ `IsTextBasedPDF()` ]({{site.info}}api/Addon_PDF.html#istextbasedpdf) .

#### Q: When is PDF Rasterizer activated?

A: Once `PDFR` has been configured, it will automatically detect if a file needs to be rasterized and if so, it will convert it to an image(s) with the set resolution(if no resolution is set, the default is 200). This happens when you call any of the following methods

> `PDFR` also works when you drag and drop the file onto the viewer to load it

* [ `LoadImage()` ]({{site.info}}api/WebTwain_IO.html#loadimage)
* [ `LoadImageEx()` ]({{site.info}}api/WebTwain_IO.html#loadimageex)
* [ `LoadImageFromBase64Binary()` ]({{site.info}}api/WebTwain_IO.html#loadimagefrombase64binary)
* [ `LoadImageFromBinary()` ]({{site.info}}api/WebTwain_IO.html#loadimagefrombinary)
* [ `FTPDownload()` ]({{site.info}}api/WebTwain_IO.html#ftpdownload)
* [ `FTPDownloadEx()` ]({{site.info}}api/WebTwain_IO.html#ftpdownloadex)
* [ `HTTPDownload()` ]({{site.info}}api/WebTwain_IO.html#httpdownload)
* [ `HTTPDownloadEx()` ]({{site.info}}api/WebTwain_IO.html#httpdownloadex)
* [ `HTTPDownloadThroughPost()` ]({{site.info}}api/WebTwain_IO.html#httpdownloadthroughpost)
* [ `HTTPDownloadDirectly()` ]({{site.info}}api/WebTwain_IO.html#httpdownloaddirectly)

### Other methods

* [ `ConvertToImage()` ]({{site.info}}api/Addon_PDF.html#converttoimage): This method proactively converts a PDF into images.
* [ `GetConvertMode()` ]({{site.info}}api/Addon_PDF.html#getconvertmode): This method returns the current convert mode.
* [ `SetPassword()` ]({{site.info}}api/Addon_PDF.html#setpassword): This method sets a password which is used to open encrypted PDF file(s).

## Output

`DWT` can output one or multiple images in the buffer as image-based PDF file(s). This feature is built into the core module and no addon is required as was covered in the [output]({{site.indepth}}features/output.html) section.

However, some advanced features are only possible with the help of the PDF addon. At present, that means configuring the resulting file(s) with the API [ `Write.Setup()` ]({{site.info}}api/Addon_PDF.html#writesetup) as shown below

``` javascript
DWObject.Addon.PDF.Write.Setup({
    author: "Dynamsoft-Support-Team",
    compression: Dynamsoft.EnumDWT_PDFCompressionType.PDF_JP2000,
    creator: "DWT",
    creationDate: "D:20200930",
    keyWords: "TWAIN, DWT, Dynamsoft",
    modifiedDate: "D:20200930",
    producer: "Dynamsoft Corporation",
    subject: "Demoing File",
    title: "Sample PDF Made by DWT",
    version: 1.5,
    quality: 80
});
DWObject.IfShowFileDialog = true;
DWObject.SaveAllAsPDF(' ', function() {}, function() {})
```
