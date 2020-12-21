---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API Reference - Index
keywords: Dynamic Web TWAIN, Documentation, API Reference, Index
breadcrumbText: API Reference
description: Dynamic Web TWAIN SDK Documentation API Reference Index Page
---

> Some old APIs are deprecated, check out [Deprecated Features and APIs]({{site.info}}schedule/deprecated.html)

# API List

## Global

* [Dynamsoft.WebTwainEnv]({{site.info}}api/Dynamsoft_WebTwainEnv.html) 
* [Dynamsoft.Enum]({{site.info}}api/Dynamsoft_Enum.html) 

## WebTwain

### Buffer

#### Methods

<!--* [GetImageBitDepthAsync()]({{site.info}}api/WebTwain_Buffer.html#getimagebitdepthasync)-->

* [ClearImageTags()]({{site.info}}api/WebTwain_Buffer.html#clearimagetags) 
* [FilterImagesByTag()]({{site.info}}api/WebTwain_Buffer.html#filterimagesbytag)
* [SetDefaultTag()]({{site.info}}api/WebTwain_Buffer.html#setdefaulttag) 
* [TagImages()]({{site.info}}api/WebTwain_Buffer.html#tagimages)
* [GetImageBitDepth()]({{site.info}}api/WebTwain_Buffer.html#getimagebitdepth)
* [GetImageSize()]({{site.info}}api/WebTwain_Buffer.html#getimagesize)
* [GetImageSizeWithSpecifiedType()]({{site.info}}api/WebTwain_Buffer.html#getimagesizewithspecifiedtype) 
* [GetSelectedImagesSize()]({{site.info}}api/WebTwain_Buffer.html#getselectedimagessize)
* [GetImageHeight()]({{site.info}}api/WebTwain_Buffer.html#getimageheight) 
* [GetImageWidth()]({{site.info}}api/WebTwain_Buffer.html#getimagewidth)
* [GetImagePartURL()]({{site.info}}api/WebTwain_Buffer.html#getimageparturl) 
* [GetImageURL()]({{site.info}}api/WebTwain_Buffer.html#getimageurl)
* [GetImageXResolution()]({{site.info}}api/WebTwain_Buffer.html#getimagexresolution) 
* [GetImageYResolution()]({{site.info}}api/WebTwain_Buffer.html#getimageyresolution)
* [GetSkewAngle()]({{site.info}}api/WebTwain_Buffer.html#getskewangle) 
* [GetSkewAngleEx()]({{site.info}}api/WebTwain_Buffer.html#getskewangleex)
* [ImageIDToIndex()]({{site.info}}api/WebTwain_Buffer.html#imageidtoindex) 
* [IndexToImageID()]({{site.info}}api/WebTwain_Buffer.html#indextoimageid)
* [IsBlankImage()]({{site.info}}api/WebTwain_Buffer.html#isblankimage) 
* [IsBlankImageExpress()]({{site.info}}api/WebTwain_Buffer.html#isblankimageexpress)
* [SelectAllImages()]({{site.info}}api/WebTwain_Buffer.html#selectallimages) 
* [SelectImages()]({{site.info}}api/WebTwain_Buffer.html#selectimages)
* [MoveImage()]({{site.info}}api/WebTwain_Buffer.html#moveimage) 
* [SwitchImage()]({{site.info}}api/WebTwain_Buffer.html#switchimage)
* [RemoveImage()]({{site.info}}api/WebTwain_Buffer.html#removeimage) 
* [RemoveAllImages()]({{site.info}}api/WebTwain_Buffer.html#removeallimages)
* [RemoveAllSelectedImages()]({{site.info}}api/WebTwain_Buffer.html#removeallselectedimages)

<!--* [RemoveAllImagesAsync()]({{site.info}}api/WebTwain_Buffer.html#removeallimagesasync)-->
<!--* [RemoveAllSelectedImagesAsync()]({{site.info}}api/WebTwain_Buffer.html#removeallselectedimagesasync)-->

#### Properties

* [BlankImageCurrentStdDev]({{site.info}}api/WebTwain_Buffer.html#blanimagecurrentstddev)   
* [BlankImageMaxStdDev]({{site.info}}api/WebTwain_Buffer.html#blankimagemaxstddev)
* [BlankImageThreshold]({{site.info}}api/WebTwain_Buffer.html#blankimagethreshold)   
* [BufferMemoryLimit]({{site.info}}api/WebTwain_Buffer.html#buffermemorylimit)
* [CurrentImageIndexInBuffer]({{site.info}}api/WebTwain_Buffer.html#currentimageindexinbuffer) 
* [HowManyImagesInBuffer]({{site.info}}api/WebTwain_Buffer.html#howmanyimagesinbuffer)
* [IfAllowLocalCache]({{site.info}}api/WebTwain_Buffer.html#ifallowlocalcache)   
* [SelectedImagesIndices]({{site.info}}api/WebTwain_Buffer.html#selectedimagesindices)
* [MaxImagesInBuffer]({{site.info}}api/WebTwain_Buffer.html#maximagesinbuffer)

#### Events

* [OnBitmapChanged]({{site.info}}api/WebTwain_Buffer.html#onbitmapchanged)
* [OnImageAreaSelected]({{site.info}}api/WebTwain_Buffer.html#onimageareaselected)
* [OnImageAreaDeSelected]({{site.info}}api/WebTwain_Buffer.html#onimageareadeselected)
* [OnIndexChangeDragDropDone]({{site.info}}api/WebTwain_Buffer.html#onindexchangedragdropdone)
* [OnTopImageInTheViewChanged]({{site.info}}api/WebTwain_Buffer.html#ontopimageintheviewchanged)

### Edit

#### Methods

* [Crop()]({{site.info}}api/WebTwain_Edit.html#crop) 
* [CropToClipboard()]({{site.info}}api/WebTwain_Edit.html#croptoclipboard)
* [CutFrameToClipboard()]({{site.info}}api/WebTwain_Edit.html#cutframetoclipboard) 
* [CutToClipboard()]({{site.info}}api/WebTwain_Edit.html#cuttoclipboard)
* [CopyToClipboard()]({{site.info}}api/WebTwain_Edit.html#copytoclipboard) 
* [Erase()]({{site.info}}api/WebTwain_Edit.html#erase)
* [Flip()]({{site.info}}api/WebTwain_Edit.html#flip)
* [Mirror()]({{site.info}}api/WebTwain_Edit.html#mirror)
* [Rotate()]({{site.info}}api/WebTwain_Edit.html#rotate) 
* [RotateEx()]({{site.info}}api/WebTwain_Edit.html#rotateex)
* [RotateLeft()]({{site.info}}api/WebTwain_Edit.html#rotateleft) 
* [RotateRight()]({{site.info}}api/WebTwain_Edit.html#rotateright)
* [ChangeBitDepth()]({{site.info}}api/WebTwain_Edit.html#changebitdepth) 
* [SetDPI()]({{site.info}}api/WebTwain_Edit.html#setdpe)
* [ConvertToBW()]({{site.info}}api/WebTwain_Edit.html#converttobw) 
* [ConvertToGrayScale()]({{site.info}}api/WebTwain_Edit.html#converttograyscale)
* [ChangeImageSize()]({{site.info}}api/WebTwain_Edit.html#changeimagesize) 
* [Invert()]({{site.info}}api/WebTwain_Edit.html#invert)
* [SetImageWidth()]({{site.info}}api/WebTwain_Edit.html#setimagewidth) 
* [ShowImageEditor()]({{site.info}}api/WebTwain_Edit.html#showimageeditor)

<!--* [FlipAsync()]({{site.info}}api/WebTwain_Edit.html#flipasync)-->
<!--* [MirrorAsync()]({{site.info}}api/WebTwain_Edit.html#mirrorasync)-->
<!--* [RotateAsync()]({{site.info}}api/WebTwain_Edit.html#rotate) -->
<!--* [RotateLeftAsync()]({{site.info}}api/WebTwain_Edit.html#rotateleft) -->
<!--* [RotateRightAsync()]({{site.info}}api/WebTwain_Edit.html#rotateright)-->
<!--* [ConvertToGrayScaleAsync()]({{site.info}}api/WebTwain_Edit.html#converttograyscaleasync)-->

#### Properties

* [BackgroundFillColor]({{site.info}}api/WebTwain_Edit.html#backgroundfillcolor)

### Scan

#### Methods

* [GetSourceNameItems()]({{site.info}}api/WebTwain_Acquire.html#getsourcenameitems) 
* [GetSourceNames()]({{site.info}}api/WebTwain_Acquire.html#getsourcenames)
* [GetSourceNamesAsync()]({{site.info}}api/WebTwain_Acquire.html#getsourcenamesasync)
* [GetDeviceType()]({{site.info}}api/WebTwain_Acquire.html#getdevicetype)
* [SelectSource()]({{site.info}}api/WebTwain_Acquire.html#selectsource)
* [SelectSourceAsync()]({{site.info}}api/WebTwain_Acquire.html#selectsourceasync)
* [SelectSourceByIndex()]({{site.info}}api/WebTwain_Acquire.html#selectsourcebyindex) 
* [SelectSourceByIndexAsync()]({{site.info}}api/WebTwain_Acquire.html#selectsourcebyindexasync) 
* [SetOpenSourceTimeout()]({{site.info}}api/WebTwain_Acquire.html#setopensourcetimeout)
* [OpenSource()]({{site.info}}api/WebTwain_Acquire.html#opensource)
* [OpenSourceAsync()]({{site.info}}api/WebTwain_Acquire.html#opensourceasync)
* [EnableSourceUI()]({{site.info}}api/WebTwain_Acquire.html#enablesourceui)
* [EnableSource()]({{site.info}}api/WebTwain_Acquire.html#enablesource)
* [AcquireImage()]({{site.info}}api/WebTwain_Acquire.html#acquireimage)
* [startScan()]({{site.info}}api/WebTwain_Acquire.html#startscan)
* [DisableSource()]({{site.info}}api/WebTwain_Acquire.html#disablesource)
* [CloseSource()]({{site.info}}api/WebTwain_Acquire.html#closesource)
* [CloseSourceAsync()]({{site.info}}api/WebTwain_Acquire.html#closesourceasync)
* [CloseWorkingProcess()]({{site.info}}api/WebTwain_Acquire.html#closeworkingprocess)

#### Properties

* [CurrentSourceName]({{site.info}}api/WebTwain_Acquire.html#currentsourcename) 
* [IfDisableSourceAfterAcquire]({{site.info}}api/WebTwain_Acquire.html#ifdisablesourceafteracquire)
* [IfDuplexEnabled]({{site.info}}api/WebTwain_Acquire.html#ifduplexenabled)  
* [IfFeederEnabled]({{site.info}}api/WebTwain_Acquire.html#iffeederenabled)
* [PageSize]({{site.info}}api/WebTwain_Acquire.html#pagesize)  
* [PixelType]({{site.info}}api/WebTwain_Acquire.html#pixeltype)
* [Resolution]({{site.info}}api/WebTwain_Acquire.html#resolution) 
* [SourceCount]({{site.info}}api/WebTwain_Acquire.html#sourcecount)

#### Events

* [OnPostAllTransfers]({{site.info}}api/WebTwain_Acquire.html#onpostalltransfers)   
* [OnPostTransfer]({{site.info}}api/WebTwain_Acquire.html#onposttransfer)
* [OnPostTransferAsync]({{site.info}}api/WebTwain_Acquire.html#onposttransferasync) 
* [OnPreAllTransfers]({{site.info}}api/WebTwain_Acquire.html#onprealltransfers)
* [OnPreTransfer]({{site.info}}api/WebTwain_Acquire.html#onpretransfer)

> The following APIs are compatible with TWAIN (mostly Windows, but could also be macOS)

#### Methods

* [CancelAllPendingTransfers()]({{site.info}}api/WebTwain_Acquire.html#cancelallpendingtransfers) 
* [CloseSourceManager()]({{site.info}}api/WebTwain_Acquire.html#closesourcemanager)
* [FeedPage()]({{site.info}}api/WebTwain_Acquire.html#feedpage)   
* [GetCustomDSData()]({{site.info}}api/WebTwain_Acquire.html#getcustomdsdata)
* [GetCustomDSDataEx()]({{site.info}}api/WebTwain_Acquire.html#getcustomdsdataex)   
* [OpenSourceManager()]({{site.info}}api/WebTwain_Acquire.html#opensourcemanager)
* [ResetImageLayout()]({{site.info}}api/WebTwain_Acquire.html#resetimagelayout)  
* [RewindPage()]({{site.info}}api/WebTwain_Acquire.html#rewindpage)
* [SetCustomDSData()]({{site.info}}api/WebTwain_Acquire.html#setcustomdsdata) 
* [SetCustomDSDataEx()]({{site.info}}api/WebTwain_Acquire.html#setcustomdsdataex)
* [SetFileXferInfo()]({{site.info}}api/WebTwain_Acquire.html#setfilexferinfo) 
* [SetImageLayout()]({{site.info}}api/WebTwain_Acquire.html#setimagelayout)
* [getCapabilities]({{site.info}}api/WebTwain_Acquire.html#getcapabilities)   
* [setCapabilities]({{site.info}}api/WebTwain_Acquire.html#setcapabilities)

#### Properties

* [BitDepth ]({{site.info}}api/WebTwain_Acquire.html#bitdepth)  
* [Brightness]({{site.info}}api/WebTwain_Acquire.html#brightness)
* [Contrast]({{site.info}}api/WebTwain_Acquire.html#contrast)   
* [DataSourceStatus]({{site.info}}api/WebTwain_Acquire.html#datasourcestatus)
* [DefaultSourceName]({{site.info}}api/WebTwain_Acquire.html#defaultsourcename)   
* [Duplex]({{site.info}}api/WebTwain_Acquire.html#duplex)
* [IfAutoBright]({{site.info}}api/WebTwain_Acquire.html#ifautobright)    
* [IfAutoDiscardBlankpages]({{site.info}}api/WebTwain_Acquire.html#ifautodiscardblankpages)
* [IfAutoFeed]({{site.info}}api/WebTwain_Acquire.html#ifautofeed)  
* [IfAutomaticBorderDetection]({{site.info}}api/WebTwain_Acquire.html#ifautomaticborderdetection)
* [IfAutomaticDeskew]({{site.info}}api/WebTwain_Acquire.html#ifautomaticdeskew)   
* [IfAutoScan]({{site.info}}api/WebTwain_Acquire.html#ifautoscan)
* [IfFeederLoaded]({{site.info}}api/WebTwain_Acquire.html#iffeederloaded)   
* [IfPaperDetectable]({{site.info}}api/WebTwain_Acquire.html#ifpaperdetectable)
* [IfShowIndicator]({{site.info}}api/WebTwain_Acquire.html#ifshowindicator) 
* [IfShowUI]({{site.info}}api/WebTwain_Acquire.html#ifshowui)
* [IfUIControllable]({{site.info}}api/WebTwain_Acquire.html#ifuicontrollable)  
* [IfUseTwainDSM]({{site.info}}api/WebTwain_Acquire.html#ifusetwaindsm)
* [ImageCaptureDriverType]({{site.info}}api/WebTwain_Acquire.html#imagecapturedrivertype)
* [ImageLayoutDocumentNumber]({{site.info}}api/WebTwain_Acquire.html#imagelayoutdocumentnumber) 
* [ImageLayoutFrameBottom]({{site.info}}api/WebTwain_Acquire.html#imagelayoutframebottom)
* [ImageLayoutFrameLeft]({{site.info}}api/WebTwain_Acquire.html#imagelayoutframeleft) 
* [ImageLayoutFrameNumber]({{site.info}}api/WebTwain_Acquire.html#imagelayoutframenumber)
* [ImageLayoutFrameRight]({{site.info}}api/WebTwain_Acquire.html#imagelayoutframeright)  
* [ImageLayoutFrameTop]({{site.info}}api/WebTwain_Acquire.html#imagelayoutframetop)
* [ImageLayoutPageNumber]({{site.info}}api/WebTwain_Acquire.html#imagelayoutpagenumber)  
* [ImagePixelType]({{site.info}}api/WebTwain_Acquire.html#imagepixeltype)
* [MagData]({{site.info}}api/WebTwain_Acquire.html#magdata) 
* [MagType]({{site.info}}api/WebTwain_Acquire.html#magtype)
* [PendingXfers]({{site.info}}api/WebTwain_Acquire.html#pendingxfers)   
* [PixelFlavor]({{site.info}}api/WebTwain_Acquire.html#pixelflavor)
* [TransferMode]({{site.info}}api/WebTwain_Acquire.html#transfermode)    
* [Unit]({{site.info}}api/WebTwain_Acquire.html#unit)
* [XferCount]({{site.info}}api/WebTwain_Acquire.html#xfercount)

#### Events

* [OnSourceUIClose]({{site.info}}api/WebTwain_Acquire.html#onsourceuiclose)

### Input

#### Methods

* [LoadImage()]({{site.info}}api/WebTwain_IO.html#loadimage)
* [LoadImageEx()]({{site.info}}api/WebTwain_IO.html#loadimageex)
* [LoadImageFromBase64Binary()]({{site.info}}api/WebTwain_IO.html#loadimagefrombase64binary)
* [LoadImageFromBinary()]({{site.info}}api/WebTwain_IO.html#loadimagefrombinary)
* [LoadDibFromClipboard()]({{site.info}}api/WebTwain_IO.html#loaddibfromclipboard)
* [FTPDownload()]({{site.info}}api/WebTwain_IO.html#ftpdownload)
* [FTPDownloadEx()]({{site.info}}api/WebTwain_IO.html#ftpdownloadex)
* [HTTPDownload()]({{site.info}}api/WebTwain_IO.html#httpdownload)
* [HTTPDownloadEx()]({{site.info}}api/WebTwain_IO.html#httpdownloadex)
* [HTTPDownloadThroughPost()]({{site.info}}api/WebTwain_IO.html#httpdownloadthroughpost)
* [HTTPDownloadDirectly()]({{site.info}}api/WebTwain_IO.html#httpdownloaddirectly)

<!--* [LoadDibFromClipboardAsync()]({{site.info}}api/WebTwain_IO.html#loaddibfromclipboardasync)-->

### Output

#### Methods

* [ConvertToBase64()]({{site.info}}api/WebTwain_IO.html#converttobase64)
* [ConvertToBlob()]({{site.info}}api/WebTwain_IO.html#converttoblob)
* [FTPUpload()]({{site.info}}api/WebTwain_IO.html#ftpupload)
* [FTPUploadEx()]({{site.info}}api/WebTwain_IO.html#ftpuploadex)
* [FTPUploadAllAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#ftpuploadallasmultipagetiff)
* [FTPUploadAllAsPDF()]({{site.info}}api/WebTwain_IO.html#ftpuploadallaspdf)
* [FTPUploadAsMultiPagePDF()]({{site.info}}api/WebTwain_IO.html#ftpuploadasmultipagepdf)
* [FTPUploadAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#ftpuploadasmultipagetiff)
* [HTTPUpload()]({{site.info}}api/WebTwain_IO.html#httpupload)
* [HTTPUploadThroughPutEx()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughputex)
* [HTTPUploadThroughPost()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughpost)
* [HTTPUploadThroughPostEx()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughpostex)
* [HTTPUploadAllThroughPostAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#httpuploadallthroughpostasmultipagetiff)
* [HTTPUploadAllThroughPostAsPDF()]({{site.info}}api/WebTwain_IO.html#httpuploadallthroughpostaspdf)
* [HTTPUploadThroughPostAsMultiPagePDF()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughpostasmultipagepdf)
* [HTTPUploadThroughPostAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughpostasmultipagetiff)
* [HTTPUploadThroughPostDirectly()]({{site.info}}api/WebTwain_IO.html#httpuploadthroughpostdirectly)
* [SaveAsBMP()]({{site.info}}api/WebTwain_IO.html#saveasbmp)
* [SaveAsJPEG()]({{site.info}}api/WebTwain_IO.html#saveasjpeg)
* [SaveAsPDF()]({{site.info}}api/WebTwain_IO.html#saveaspdf)
* [SaveAsPNG()]({{site.info}}api/WebTwain_IO.html#saveaspng)
* [SaveAsTIFF()]({{site.info}}api/WebTwain_IO.html#saveastiff)
* [SaveSelectedImagesAsMultiPagePDF()]({{site.info}}api/WebTwain_IO.html#saveselectedimagesasmultipagepdf)
* [SaveSelectedImagesAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#saveselectedimagesasmultipagetiff)
* [SaveAllAsMultiPageTIFF()]({{site.info}}api/WebTwain_IO.html#saveallasmultipagetiff)
* [SaveAllAsPDF()]({{site.info}}api/WebTwain_IO.html#saveallaspdf)

### Others

#### Methods

* [ClearTiffCustomTag()]({{site.info}}api/WebTwain_IO.html#cleartiffcustomtag)    
* [SetTiffCustomTag()]({{site.info}}api/WebTwain_IO.html#settiffcustomtag)
* [ClearAllHTTPFormField()]({{site.info}}api/WebTwain_IO.html#clearallhttpformfield) 
* [SetHTTPFormField()]({{site.info}}api/WebTwain_IO.html#sethttpformfield)
* [SetHTTPHeader()]({{site.info}}api/WebTwain_IO.html#sethttpheader)   
* [SetUploadSegment()]({{site.info}}api/WebTwain_IO.html#setuploadsegment)
* [ShowFileDialog()]({{site.info}}api/WebTwain_IO.html#showfiledialog) 
* [Print()]({{site.info}}api/WebTwain_IO.html#print)

#### Properties

* [FTPPassword]({{site.info}}api/WebTwain_IO.html#ftppassword)  
* [FTPPort]({{site.info}}api/WebTwain_IO.html#ftpport)
* [FTPUserName]({{site.info}}api/WebTwain_IO.html#ftpusername)  
* [IfPASVMode]({{site.info}}api/WebTwain_IO.html#ifpasvmode)
* [HttpFieldNameOfUploadedImage]({{site.info}}api/WebTwain_IO.html#httpfieldnameofuploadedimage) 
* [HTTPPort]({{site.info}}api/WebTwain_IO.html#httpport)
* [IfSSL]({{site.info}}api/WebTwain_IO.html#ifssl)  
* [HTTPPostResponseString]({{site.info}}api/WebTwain_IO.html#httppostresponsestring)
* [IfShowFileDialog]({{site.info}}api/WebTwain_IO.html#ifshowfiledialog) 
* [IfShowCancelDialogWhenImageTransfer]({{site.info}}api/WebTwain_IO.html#ifshowcanceldialogwhenimagetransfer)
* [IfShowProgressBar]({{site.info}}api/WebTwain_IO.html#ifshowprogressbar)  
* [JPEGQuality]()
* [IfTiffMultiPage]({{site.info}}api/WebTwain_IO.html#iftiffmultipage)   
* [TIFFCompressionType]({{site.info}}api/WebTwain_IO.html#tiffcompressiontype)
* [MaxUploadImageSize]({{site.info}}api/WebTwain_IO.html#maxuploadimagesize)
* [IfAppendImage]({{site.info}}api/WebTwain_IO.html#ifappendimage)

#### Events

* [OnGetFilePath]({{site.info}}api/WebTwain_IO.html#ongetfilepath)
* [OnPostLoad]({{site.info}}api/WebTwain_IO.html#onpostload)
* [OnInternetTransferPercentage]({{site.info}}api/WebTwain_IO.html#oninternettransferpercentage)

### Util

#### Methods

* [RegisterEvent()]({{site.info}}api/WebTwain_Util.html#registerevent) 
* [UnregisterEvent()]({{site.info}}api/WebTwain_Util.html#unregisterevent)
* [SetProductKeyAsync()]({{site.info}}api/WebTwain_Util.html#setproductkeyasync)
* [SetLanguage()]({{site.info}}api/WebTwain_Util.html#setlanguage)
* [GenerateURLForUploadData()]({{site.info}}api/WebTwain_Util.html#generateurlforuploaddata)

#### Properties

* [ErrorCode]({{site.info}}api/WebTwain_Util.html#errorcode)
* [ErrorString]({{site.info}}api/WebTwain_Util.html#errorstring)
* [LogLevel]({{site.info}}api/WebTwain_Util.html#loglevel)
* [Manufacturer]({{site.info}}api/WebTwain_Util.html#manufacturer)
* [ProductFamily]({{site.info}}api/WebTwain_Util.html#productfamily)
* [ProductName]({{site.info}}api/WebTwain_Util.html#productname)
* [VersionInfo]({{site.info}}api/WebTwain_Util.html#versioninfo)
* [ProductKey]({{site.info}}api/WebTwain_Util.html#productkey)
* [UseLocalService]({{site.info}}api/WebTwain_Util.html#uselocalservice)

### Viewer

> For WebTwain instances

#### Methods

* [BindViewer()]({{site.info}}api/WebTwain_Viewer.html#bindviewer)
* [UnbindViewer()]({{site.info}}api/WebTwain_Viewer.html#unbindviewer)
* [UpdateViewer()]({{site.info}}api/WebTwain_Viewer.html#updateviewer)

#### Properties

* [BackgroundColor]({{site.info}}api/WebTwain_Viewer.html#backgroundcolor) 
* [SelectionImageBorderColor]({{site.info}}api/WebTwain_Viewer.html#selectionimagebordercolor)
* [FitWindowType]({{site.info}}api/WebTwain_Viewer.html#fitwindowtype)  
* [IfFitWindow]({{site.info}}api/WebTwain_Viewer.html#iffitwindow)
* [Height]({{site.info}}api/WebTwain_Viewer.html#height)  
* [Width]({{site.info}}api/WebTwain_Viewer.html#width)
* [IfAutoScroll]({{site.info}}api/WebTwain_Viewer.html#ifautoscroll)    
* [ShowPageNumber]({{site.info}}api/WebTwain_Viewer.html#showpagenumber)
* [MouseX]({{site.info}}api/WebTwain_Viewer.html#mousex)  
* [MouseY]({{site.info}}api/WebTwain_Viewer.html#mousey)
* [ImageMargin]({{site.info}}api/WebTwain_Viewer.html#imagemargin)  
* [MouseShape]({{site.info}}api/WebTwain_Viewer.html#mouseshape)
* [SelectionRectAspectRatio]({{site.info}}api/WebTwain_Buffer.html#selectionrectaspectratio)
* [Zoom]({{site.info}}api/WebTwain_Viewer.html#zoom)

#### Events

* [OnMouseClick]({{site.info}}api/WebTwain_Viewer.html#onmouseclick) 
* [OnMouseDoubleClick]({{site.info}}api/WebTwain_Viewer.html#onmousedoubleclick)
* [OnMouseMove]({{site.info}}api/WebTwain_Viewer.html#onmousemove)   
* [OnMouseRightClick]({{site.info}}api/WebTwain_Viewer.html#onmouserightclick)

> For the WebTwain. Viewer interface

#### Methods

* [setViewMode()]({{site.info}}api/WebTwain_Viewer.html#setviewmode) 
* [updateUISettings()]({{site.info}}api/WebTwain_Viewer.html#updateuisettings)
* [setButtonClass()]({{site.info}}api/WebTwain_Viewer.html#setbuttonclass)  
* [setSelectedImageArea()]({{site.info}}api/WebTwain_Viewer.html#setselectedimagearea)
* [zoomIn()]({{site.info}}api/WebTwain_Viewer.html#zoomin) 
* [zoomOut()]({{site.info}}api/WebTwain_Viewer.html#zoomout)
* [bindCustomElement]({{site.info}}api/WebTwain_Viewer.html#bindcustomelement) 
* [showCustomElement]({{site.info}}api/WebTwain_Viewer.html#showcustomelement)
* [hideCustomElement]({{site.info}}api/WebTwain_Viewer.html#hidecustomelement) 
* [toggleCustomElement]({{site.info}}api/WebTwain_Viewer.html#togglecustomelement)
* [showVideo()]({{site.info}}api/WebTwain_Viewer.html#showvideo)
* [closeVideo()]({{site.info}}api/WebTwain_Viewer.html#closevideo)
* [on()]({{site.info}}api/WebTwain_Viewer.html#on)

#### Properties

* [bOnlyShowThumbnailsView]({{site.info}}api/WebTwain_Viewer.html#bonlyshowthumbnailsview)
* [cursorOverThumbnailsView]({{site.info}}api/WebTwain_Viewer.html#cursoroverthumbnailsview)

#### Events

* [video-closed]({{site.info}}api/WebTwain_Viewer.html#vidoe-closed)
* [video-error]({{site.info}}api/WebTwain_Viewer.html#vidoe-error)

## Addon

### BarcodeReader

#### Methods

* [decode()]({{site.info}}api/Addon_BarcodeReader.html#decode)
* [getRuntimeSettings()]({{site.info}}api/Addon_BarcodeReader.html#getruntimesettings)
* [updateRuntimeSettings()]({{site.info}}api/Addon_BarcodeReader.html#updateruntimesettings)
* [resetRuntimeSettings()]({{site.info}}api/Addon_BarcodeReader.html#resetruntimesettings)
* [initRuntimeSettingsWithString()]({{site.info}}api/Addon_BarcodeReader.html#initruntimesettingswithstring)

### OCR

#### Methods

* [Download()]({{site.info}}api/Addon_OCR.html#download)  
* [DownloadLangData()]({{site.info}}api/Addon_OCR.html#downloadlangdata)
* [IsModuleInstalled()]({{site.info}}api/Addon_OCR.html#ismoduleinstalled)   
* [SetLanguage()]({{site.info}}api/Addon_OCR.html#setlanguage)
* [SetOutputFormat()]({{site.info}}api/Addon_OCR.html#setoutputformat) 
* [SetPageSetMode()]({{site.info}}api/Addon_OCR.html#setpagesetmode)
* [GetIfUseDetectedFont()]({{site.info}}api/Addon_OCR.html#getifusedetectedfont)    
* [SetIfUseDetectedFont()]({{site.info}}api/Addon_OCR.html#setifusedetectedfont)
* [GetUnicodeFontName()]({{site.info}}api/Addon_OCR.html#getunicodefontname) 
* [SetUnicodeFontName()]({{site.info}}api/Addon_OCR.html#setunicodefontname)
* [GetMinFontSizeforMoreAccurateResult()]({{site.info}}api/Addon_OCR.html#getminfontsizeformoreaccurateresult) 
* [SetMinFontSizeforMoreAccurateResult()]({{site.info}}api/Addon_OCR.html#setminfontsizeformoreaccurateresult)
* [Recognize()]({{site.info}}api/Addon_OCR.html#recognize)    
* [RecognizeFile()]({{site.info}}api/Addon_OCR.html#recognizefile)
* [RecognizeRect()]({{site.info}}api/Addon_OCR.html#recognizerect) 
* [RecognizeSelectedImages()]({{site.info}}api/Addon_OCR.html#recognizeselectedimages)

### OCRPro

#### Methods

* [Download()]({{site.info}}api/Addon_OCRPro.html#download) 
* [IsModuleInstalled()]({{site.info}}api/Addon_OCRPro.html#ismoduleinstalled)
* [Recognize()]({{site.info}}api/Addon_OCRPro.html#recognize)  
* [RecognizeFile()]({{site.info}}api/Addon_OCRPro.html#recognizefile)
* [RecognizeRect()]({{site.info}}api/Addon_OCRPro.html#recognizerect) 
* [RecognizeSelectedImages()]({{site.info}}api/Addon_OCRPro.html#recognizeselectedimages)

#### Properties

* [Settings]({{site.info}}api/Addon_OCRPro.html#settings)

### PDF

#### Methods

* [IsTextBasedPDF()]({{site.info}}api/Addon_PDF.html#istextbasedpdf)
* [SetConvertMode()]({{site.info}}api/Addon_PDF.html#setconvertmode)
* [SetPassword()]({{site.info}}api/Addon_PDF.html#setpassword)
* [SetResolution()]({{site.info}}api/Addon_PDF.html#setresolution)
* [Write. Setup()]({{site.info}}api/Addon_PDF.html#writesetup)

### Camera

#### Methods

* [getSourceList()]({{site.info}}api/Addon_Camera.html#getsourcelist) 
* [selectSource()]({{site.info}}api/Addon_Camera.html#selectsource)
* [getCurrentSource()]({{site.info}}api/Addon_Camera.html#getcurrentsource)
* [closeSource()]({{site.info}}api/Addon_Camera.html#closesource)
* [getResolution()]({{site.info}}api/Addon_Camera.html#getresolution)
* [setResolution()]({{site.info}}api/Addon_Camera.html#setresolution)
* [getCurrentResolution()]({{site.info}}api/Addon_Camera.html#getcurrentresolution)
* [play()]({{site.info}}api/Addon_Camera.html#play)
* [pause()]({{site.info}}api/Addon_Camera.html#pause)
* [resume()]({{site.info}}api/Addon_Camera.html#resume)
* [stop()]({{site.info}}api/Addon_Camera.html#stop)
* [getStatus()]({{site.info}}api/Addon_Camera.html#getstatus)
* [capture()]({{site.info}}api/Addon_Camera.html#capture)

### Webcam

#### Methods

* [CaptureImage()]({{site.info}}api/Addon_Webcam.html#captureimage) 
* [CloseSource()]({{site.info}}api/Addon_Webcam.html#closesource)
* [GetCameraControlPropertySetting()]({{site.info}}api/Addon_Webcam.html#getcameracontrolpropertysetting) 
* [GetCameraControlPropertyMoreSetting()]({{site.info}}api/Addon_Webcam.html#getcameracontrolpropertymoresetting)
* [GetVideoPropertySetting()]({{site.info}}api/Addon_Webcam.html#getvideopropertysetting) 
* [GetVideoPropertyMoreSetting()]({{site.info}}api/Addon_Webcam.html#getvideopropertymoresetting)
* [SetCameraControlPropertySetting()]({{site.info}}api/Addon_Webcam.html#setcameracontrolpropertysetting)
* [SetVideoPropertySetting()]({{site.info}}api/Addon_Webcam.html#setvideopropertysetting)
* [GetFrameRate()]({{site.info}}api/Addon_Webcam.html#getframerate) 
* [SetFrameRate()]({{site.info}}api/Addon_Webcam.html#setframerate)
* [GetMediaType()]({{site.info}}api/Addon_Webcam.html#getmediatype) 
* [SetMediaType()]({{site.info}}api/Addon_Webcam.html#setmediatype)
* [GetResolution()]({{site.info}}api/Addon_Webcam.html#getresolution) 
* [SetResolution()]({{site.info}}api/Addon_Webcam.html#setresolution)
* [GetFramePartURL()]({{site.info}}api/Addon_Webcam.html#getframeparturl) 
* [GetFrameURL()]({{site.info}}api/Addon_Webcam.html#getframeurl)
* [GetSourceList()]({{site.info}}api/Addon_Webcam.html#getsourcelist)  
* [SelectSource()]({{site.info}}api/Addon_Webcam.html#selectsource)
* [PauseVideo()]({{site.info}}api/Addon_Webcam.html#pausevideo) 
* [PlayVideo()]({{site.info}}api/Addon_Webcam.html#playvideo)
* [SetVideoRotateMode()]({{site.info}}api/Addon_Webcam.html#setvideorotatemode)    
* [StopVideo()]({{site.info}}api/Addon_Webcam.html#stopvideo)

## [Dynamsoft. FileUploader](#dynamsoftfileuploader)

#### Methods

* [Init()]({{site.info}}api/Dynamsoft_FileUploader.html#init)
* [CreateJob()]({{site.info}}api/Dynamsoft_FileUploader.html#createjob)
* [Run()]({{site.info}}api/Dynamsoft_FileUploader.html#run)
* [Cancel()]({{site.info}}api/Dynamsoft_FileUploader.html#cancel)
* [CancelAllUpload()]({{site.info}}api/Dynamsoft_FileUploader.html#cancelallupload)
