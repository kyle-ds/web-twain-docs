---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API Reference - Acquire APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Acquire APIs
breadcrumbText: Acquire
description: Dynamic Web TWAIN SDK Documentation API Reference Acquire APIs Page
---

# WebTwain Scan

> The following APIs are compatible with  TWAIN | ICA | SANE (Windows, macOS and Linux)

**Methods**

* [GetSourceNameItems()](#getsourcenameitems) 
* [GetSourceNames()](#getsourcenames)
* [GetSourceNamesAsync()](#getsourcenamesasync)
* [GetDeviceType()](#getdevicetype)
* [SelectSource()](#selectsource)
* [SelectSourceAsync()](#selectsourceasync)
* [SelectSourceByIndex()](#selectsourcebyindex) 
* [SelectSourceByIndexAsync()](#selectsourcebyindexasync) 
* [SetOpenSourceTimeout()](#setopensourcetimeout)
* [OpenSource()](#opensource)
* [OpenSourceAsync()](#opensourceasync)
* [EnableSourceUI()](#enablesourceui)
* [EnableSource()](#enablesource)
* [AcquireImage()](#acquireimage)
* [startScan()](#startscan)
* [DisableSource()](#disablesource)
* [CloseSource()](#closesource)
* [CloseSourceAsync()](#closesourceasync)
* [CloseWorkingProcess](#closeworkingprocess)

**Properties**

* [CurrentSourceName](#currentsourcename) 
* [IfDisableSourceAfterAcquire](#ifdisablesourceafteracquire)
* [IfDuplexEnabled](#ifduplexenabled) 
* [IfFeederEnabled](#iffeederenabled)
* [PageSize](#pagesize) 
* [PixelType](#pixeltype)
* [Resolution](#resolution) 
* [SourceCount](#sourcecount)

**Events**

* [OnPostAllTransfers](#onpostalltransfers) 
* [OnPostTransfer](#onposttransfer)
* [OnPostTransferAsync](#onposttransferasync) 
* [OnPreAllTransfers](#onprealltransfers)
* [OnPreTransfer](#onpretransfer)

> The following APIs are compatible with TWAIN (mostly Windows, but could also be macOS)

**Methods**

* [OpenSourceManager()](#opensourcemanager)
* [OpenSourceManagerAsync()](#opensourcemanagerasync)  
* [CloseSourceManager()](#closesourcemanager)
* [CloseSourceManagerAsync()](#closesourcemanagerasync)
* [GetCustomDSData()](#getcustomdsdata)
* [GetCustomDSDataEx()](#getcustomdsdataex) 
* [CancelAllPendingTransfers()](#cancelallpendingtransfers)
* [FeedPage()](#feedpage) 
* [ResetImageLayout()](#resetimagelayout) 
* [RewindPage()](#rewindpage)
* [SetCustomDSData()](#setcustomdsdata) 
* [SetCustomDSDataEx()](#setcustomdsdataex)
* [SetFileXferInfo()](#setfilexferinfo) 
* [SetImageLayout()](#setimagelayout)
* [getCapabilities](#getcapabilities) 
* [setCapabilities](#setcapabilities)

**Properties**

* [BitDepth ](#bitdepth) 
* [BlankImageThreshold](#blankimagethreshold) 
* [Brightness](#brightness)
* [Contrast](#contrast) 
* [DataSourceStatus](#datasourcestatus)
* [DefaultSourceName](#defaultsourcename) 
* [Duplex](#duplex)
* [IfAutoBright](#ifautobright) 
* [IfAutoDiscardBlankpages](#ifautodiscardblankpages)
* [IfAutoFeed](#ifautofeed)
* [IfAutomaticBorderDetection](#ifautomaticborderdetection)
* [IfAutomaticDeskew](#ifautomaticdeskew) 
* [IfAutoScan](#ifautoscan)
* [IfFeederLoaded](#iffeederloaded) 
* [IfPaperDetectable](#ifpaperdetectable)
* [IfShowIndicator](#ifshowindicator) 
* [IfShowUI](#ifshowui)
* [IfUIControllable](#ifuicontrollable) 
* [IfUseTwainDSM](#ifusetwaindsm)
* [ImageCaptureDriverType](#imagecapturedrivertype)
* [ImageLayoutDocumentNumber](#imagelayoutdocumentnumber) 
* [ImageLayoutFrameBottom](#imagelayoutframebottom)
* [ImageLayoutFrameLeft](#imagelayoutframeleft) 
* [ImageLayoutFrameNumber](#imagelayoutframenumber)
* [ImageLayoutFrameRight](#imagelayoutframeright) 
* [ImageLayoutFrameTop](#imagelayoutframetop)
* [ImageLayoutPageNumber](#imagelayoutpagenumber) 
* [ImagePixelType](#imagepixeltype)
* [ImageBitsPerPixel](#imagebitsperpixel) 
* [ImageLength](#imagelength)
* [ImageWidth](#imagewidth) 
* [ImageXResolution](#imagexresolution)|
* [ImageYResolution](#imageyresolution) 
* [XferCount](#xfercount)
* [MagData](#magdata) 
* [MagType](#magtype)
* [PendingXfers](#pendingxfers) 
* [PixelFlavor](#pixelflavor)
* [TransferMode](#transfermode) 
* [Unit](#unit)

**Events**

* [OnSourceUIClose](#onsourceuiclose)

---

## AcquireImage

**Syntax**

``` typescript
/**
 * Start image acquisition.
 * @param deviceConfiguration Configuration for the acquisition.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
AcquireImage(
    deviceConfiguration?: DeviceConfiguration
): void;

AcquireImage(
    successCallBack?: () => void,
    failureCallBack?: (
        errorCode: number,
        errorString: string) => void
): void;

AcquireImage(
    deviceConfiguration?: DeviceConfiguration,
    successCallBack?: () => void,
    failureCallBack?: (
        errorCode: number,
        errorString: string) => void
): void;

interface DeviceConfiguration {
    /**
     * Whether to show the built-in User Interface from the device vendor.
     * In v16.2+, it can also control whether to use the UI remotely.
     */
    IfShowUI?: boolean;
    /**
     * How a pixel is represented. Basically it means whether to scan in color, grey or black & white
     */
    PixelType?: Dynamsoft.EnumDWT_PixelType;
    /**
     * How detailed is the acquisition. Measured by dots per pixel (DPI)
     */
    Resolution?: number;
    /**
     * Whether to use the document feeder or the flatbed of the device.
     */
    IfFeederEnabled?: boolean;
    /**
     * Whether to scan one side or both sides of each paper.
     */
    IfDuplexEnabled?: boolean;
    /**
     * Whether to close the built-in User Interface after aquisition. Only valid when {IfShowUI} is true.
     */
    IfDisableSourceAfterAcquire?: boolean;
    /**
     * Whether to retrieve information about the image after it's transferred.
     */
    IfGetImageInfo?: boolean;
    /**
     * Whether to retrieve extended information about the image after it's transferred.
     */
    IfGetExtImageInfo?: boolean;
    /**
     * How much extended information is retrieved. Only valid when {IfGetExtImageInfo} is true.
     */
    extendedImageInfoQueryLevel?: number;
    /**
     * Whether to scan from a remote computer.
     * (Added in 16.2)
     */
    RemoteScan:boolean;
    /**
     * Specify a source by its index.
     * (Added in 16.2)
     */
    SelectSourceByIndex: number;
}
```

**Usage notes**

`extendedImageInfoQueryLevel` is 0 by default which means the following information will be retrieved (if available):

| Label                  | Value  |
| :--------------------- | :----- |
| TWEI_BARCODEX          | 0x1200 |
| TWEI_BARCODEY          | 0x1201 |
| TWEI_BARCODETEXT       | 0x1202 |
| TWEI_BARCODETYPE       | 0x1203 |
| TWEI_ENDORSEDTEXT      | 0x1213 |
| TWEI_BARCODECONFIDENCE | 0x121A |
| TWEI_BARCODEROTATION   | 0x121B |
| TWEI_BARCODETEXTLENGTH | 0x121C |
| TWEI_BOOKNAME          | 0x1238 |
| TWEI_CHAPTERNUMBER     | 0x1239 |
| TWEI_DOCUMENTNUMBER    | 0x123A |
| TWEI_PAGENUMBER        | 0x123B |
| TWEI_CAMERA            | 0x123C |
| TWEI_FRAMENUMBER       | 0x123D |
| TWEI_FRAME             | 0x123E |
| TWEI_PIXELFLAVOR       | 0x123F |
| TWEI_MAGDATA           | 0x1243 |
| TWEI_MAGTYPE           | 0x1244 |
| TWEI_PAGESIDE          | 0x1245 |

If it's set to 1, the following will also be retrieved (if available):

| Label | Value |
|:-|:-|
| TWEI_DESHADETOP | 0x1204 |
| TWEI_DESHADELEFT | 0x1205 |
| TWEI_DESHADEHEIGHT | 0x1206 |
| TWEI_DESHADEWIDTH | 0x1207 |
| TWEI_DESHADESIZE | 0x1208 |
| TWEI_SPECKLESREMOVED | 0x1209 |
| TWEI_HORZLINEXCOORD | 0x120A |
| TWEI_HORZLINEYCOORD | 0x120B |
| TWEI_HORZLINELENGTH | 0x120C |
| TWEI_HORZLINETHICKNESS | 0x120D |
| TWEI_VERTLINEXCOORD | 0x120E |
| TWEI_VERTLINEYCOORD | 0x120F |
| TWEI_VERTLINELENGTH | 0x1210 |
| TWEI_VERTLINETHICKNESS | 0x1211 |
| TWEI_PATCHCODE | 0x1212 |
| TWEI_FORMCONFIDENCE | 0x1214 |
| TWEI_FORMTEMPLATEMATCH | 0x1215 |
| TWEI_FORMTEMPLATEPAGEMATCH | 0x1216 |
| TWEI_FORMHORZDOCOFFSET | 0x1217 |
| TWEI_FORMVERTDOCOFFSET | 0x1218 |
| TWEI_BARCODECOUNT | 0x1219 |
| TWEI_DESHADECOUNT | 0x121D |
| TWEI_DESHADEBLACKCOUNTOLD | 0x121E |
| TWEI_DESHADEBLACKCOUNTNEW | 0x121F |
| TWEI_DESHADEBLACKRLMIN | 0x1220 |
| TWEI_DESHADEBLACKRLMAX | 0x1221 |
| TWEI_DESHADEWHITECOUNTOLD | 0x1222 |
| TWEI_DESHADEWHITECOUNTNEW | 0x1223 |
| TWEI_DESHADEWHITERLMIN | 0x1224 |
| TWEI_DESHADEWHITERLAVE | 0x1225 |
| TWEI_DESHADEWHITERLMAX | 0x1226 |
| TWEI_BLACKSPECKLESREMOVED | 0x1227 |
| TWEI_WHITESPECKLESREMOVED | 0x1228 |
| TWEI_HORZLINECOUNT | 0x1229 |
| TWEI_VERTLINECOUNT | 0x122A |
| TWEI_DESKEWSTATUS | 0x122B |
| TWEI_SKEWORIGINALANGLE | 0x122C |
| TWEI_SKEWFINALANGLE | 0x122D |
| TWEI_SKEWCONFIDENCE | 0x122E |
| TWEI_SKEWWINDOWX1 | 0x122F |
| TWEI_SKEWWINDOWY1 | 0x1230 |
| TWEI_SKEWWINDOWX2 | 0x1231 |
| TWEI_SKEWWINDOWY2 | 0x1232 |
| TWEI_SKEWWINDOWX3 | 0x1233 |
| TWEI_SKEWWINDOWY3 | 0x1234 |
| TWEI_SKEWWINDOWX4 | 0x1235 |
| TWEI_SKEWWINDOWY4 | 0x1236 |
| TWEI_ICCPROFILE | 0x1240 |
| TWEI_LASTSEGMENT | 0x1241 |
| TWEI_SEGMENTNUMBER | 0x1242 |
| TWEI_FILESYSTEMSOURCE | 0x1246 |
| TWEI_IMAGEMERGED | 0x1247 |
| TWEI_MAGDATALENGTH | 0x1248 |
| TWEI_PAPERCOUNT | 0x1249 |
| TWEI_PRINTERTEXT | 0x124A |

If it's set to 2, then besides what's mentioned in the two tables above, the Dynamci Web TWAIN library will also try to query the scanner for its own custom extended image info.

* Remote Scan

  When [scanning remotely]({{site.indepth}}feature/input.html#scan-from-a-remote-scanner), if the method is called without any parameter, [`IfShowUI`](#ifshowui) must be set to `false`.

**Example**

> The example code shows 4 ways to use the API `AcquireImage()`

``` javascript
var deviceConfiguration = {
    IfShowUI: false,
    PixelType: Dynamsoft.EnumDWT_PixelType.TWPT_RGB,
    Resolution: 300,
    IfFeederEnabled: true,
    IfDuplexEnabled: false,
    IfDisableSourceAfterAcquire: true,
    IfGetImageInfo: true,
    IfGetExtImageInfo: true,
    extendedImageInfoQueryLevel: 0
};

function successCallback() {
    console.log('successful');
}

function failureCallback(errorCode, errorString) {
    alert(errorString);
}

function AcquireImage1() {
    DWObject.SelectSource(function() {
        DWObject.OpenSource();
        DWObject.IfShowUI = false;
        DWObject.PixelType = Dynamsoft.EnumDWT_PixelType.TWPT_RGB;
        DWObject.Resolution = 300;
        DWObject.IfFeederEnabled = true;
        DWObject.IfDuplexEnabled = false;
        DWObject.IfDisableSourceAfterAcquire = true;
        DWObject.AcquireImage();
    }, failureCallback);
}

function AcquireImage2() {
    DWObject.SelectSource(function() {
        DWObject.OpenSource();
        DWObject.AcquireImage(deviceConfiguration);
    }, failureCallback);
}

function AcquireImage3() {
    DWObject.SelectSource(function() {
        DWObject.OpenSource();
        DWObject.IfShowUI = false;
        DWObject.PixelType = Dynamsoft.EnumDWT_PixelType.TWPT_RGB;
        DWObject.Resolution = 300;
        DWObject.IfFeederEnabled = true;
        DWObject.IfDuplexEnabled = false;
        DWObject.IfDisableSourceAfterAcquire = true;
        DWObject.AcquireImage(successCallback, failureCallback);
    }, failureCallback);
}

function AcquireImage4() {
    DWObject.SelectSource(function() {
        DWObject.OpenSource();
        DWObject.AcquireImage(deviceConfiguration, successCallback, failureCallback);
    }, failureCallback);
}
```

---

## CloseSource

**Syntax**

``` typescript
/**
 * Close the data source (a TWAIN/ICA/SANE device which in most cases is a scanner) to free it to be used by other applications.
 */
CloseSource(): boolean; 
```

---

## CloseSourceAsync

**Syntax**

``` typescript
/**
 * Close the data source (a TWAIN/ICA/SANE device which in most cases is a scanner) to free it to be used by other applications.
 */
CloseSourceAsync(): Promise<boolean>;
```

---

## DisableSource

**Syntax**

``` typescript
/**
 * Disable the data source (a TWAIN/ICA/SANE device which in most cases is a scanner) to stop the acquiring process. If the data source's user interface is displayed, it will be closed.
 */
DisableSource(): boolean;
```

**Usage notes**

After `DisableSource()` is called, the Source is still open and you can continue to acquire images by calling `AcquireImage()` or `EnableSource()` .

---

## EnableSource

**Syntax**

``` typescript
/**
 * Enable the data source to start the acquiring process.
 */ 
EnableSource(): boolean;
```

**Usage notes**

The method is equivalent to `AcquireImage()` without parameters.

---

## EnableSourceUI

**Syntax**

``` typescript
/**
 * Display the TWAIN source's built-in user interface.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 */
EnableSourceUI(
    successCallBack: () => void,
    failureCallBack: (
        errorCode: number,
        errorString: string) => void
): void;
```

**Usage notes**

This method enables the user to manipulate the settings for scanning but not start an actual scan. It only works if the source supports the capability `CAP_ENABLEDSUIONLY` . User can call [GetCustomDSDataEx()](#getcustomdsdataex) to save the settings in the callback `successCallBack` and later call [SetCustomDSDataEx()](#setcustomdsdataex) to apply the settings before starting a scan.

---

## OpenSource

**Syntax**

``` typescript
/**
 * Load a data source to get it ready to acquire images.
 */
OpenSource(): boolean;
```

---

## OpenSourceAsync

**Syntax**

``` typescript
/**
 * Load a data source to get it ready to acquire images.
 */
OpenSourceAsync(): Promise<boolean>;
```

---

## GetSourceNames

**Syntax**

``` typescript
/**
 * Return all available data sources (scanners, etc.) and optionally all detailed information about them.
 * @param bIncludeDetails Whether to return more details about the data sources or just their names.
 */
GetSourceNames(bIncludeDetails: boolean): string[] | ISourceDetails[];

interface SourceDetails {
    /**
     * The driver type which can be "TWAIN" | "ICA" | "SANE"
     */
    DriverType?: string;
    /**
     * Information about the driver if it's DriverType is "ICA"
     */
    DeviceInfo?: any;
    /**
     * The name of the data source. E.g. "TWAIN2 FreeImage Software Scanner".
     */
    ProductName?: string;
    /**
     * Whether it is the default source.
     */
    IsDefaultSource?: boolean;
    /**
     * Whether it is the current source.
     */
    IsCurrentSource?: boolean;
    /**
     * The family name of the data source. E.g. "Software Scan".
     */
    ProductFamily?: string;
    /**
     * The manufacturer of the data source. E.g. "TWAIN Working Group".
     */
    Manufacturer?: string;
    /**
     *
     */
    SupportedGroups?: 1073741827,
    /**
     * The version of the protocol based on which the data source is developed.
     */
    ProtocolMajor?: number;
    ProtocolMinor?: number;
    /**
     * Detailed version of the data source.
     */
    Version?: Version;
}
interface Version {
    MajorNum?: number;
    MinorNum?: number;
    Language?: number;
    Country?: number;
    Info?: string;
}
```

---

## GetSourceNamesAsync

**Syntax**

``` typescript
/**
 * Return all available data sources (scanners, etc.) and optionally all detailed information about them.
 * @param bIncludeDetails Whether to return more details about the data sources or just their names.
 */
GetSourceNamesAsync(bIncludeDetails: boolean): Promise<string[] | ISourceDetails[]>;
```

---

## SelectSource

**Syntax**

``` typescript
/**
 * Bring up the Source Selection User Interface (UI) for the user to choose a data source.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
SelectSource(
    successCallBack?: () => void,
    failureCallBack?: (errorCode: number, errorString: string) => void
): boolean | void;
```

**Usage notes**

* It's recommended to use this API asynchronously by pass arguments to the parameters `successCallback` and `failureCallback` .
* On `Windows` and `Windows` only, you can call this method with no arguments so that it runs synchronously and return a boolean value.
* When [scanning remotely]({{site.indepth}}feature/input.html#scan-from-a-remote-scanner), this method must be called asynchronously. 

**Example**

``` javascript
DWObject.SelectSource(function() {
    DWObject.OpenSource();
    DWObject.AcquireImage();
}, function(errorCode, errorString) {
    console.log(errorString);
});
```

---

## SelectSourceAsync

**Syntax**

``` typescript
/**
 * Bring up the Source Selection User Interface (UI) for the user to choose a data source.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
SelectSourceAsync(
    successCallBack?: () => void,
    failureCallBack?: (errorCode: number, errorString: string) => void
): Promise<boolean>;
```

---

## SelectSourceByIndex

**Syntax**

``` typescript
/**
 * Select a data source by its index.
 * @param index The index of the data source.
 */
SelectSourceByIndex(index: number): boolean;
```

**Example**

``` javascript
DWObject.SelectSourceByIndex(0);
DWObject.OpenSource();
DWObject.AcquireImage();
```

---

## SelectSourceByIndexAsync

**Syntax**

``` typescript
/**
 * Select a data source by its index.
 * @param index The index of the data source.
 */
SelectSourceByIndexAsync(index: number): Promise<boolean>;
```

**Example**

``` javascript
DWObject.SelectSourceByIndexAsync(0)
    .then(() =>
        return DWObject.OpenSourceAsync())
    .then(() => retyrb DWObject.AcquireImage());
```

---

## SetOpenSourceTimeout

**Syntax**

``` typescript
/**
 * Sets a timer which stops the data source opening process once it expires.
 * @param duration Define the duration of the timer (in milliseconds).
 */
SetOpenSourceTimeout(duration: number): boolean;
```

**Example**

``` javascript
DWObject.SelectSource(function() {
    DWObject.SetOpenSourceTimeout(3000);
    DWObject.OpenSource();
    DWObject.AcquireImage();
});
```

---

## startScan

**Syntax**

``` typescript
/**
 * Start the acquisition by passing all settings at once.
 * @param scanSetup Configuration for the acquisition.
 */
startScan(scanSetup: ScanSetup): Promise<IScanSetup>;

interface ScanSetup {
  /**
   * An id that specifies this specific setup.
   */
  setupId?: string,
  /**
   * Whether to ignore or fail the acquistion when an exception is raised. Set "ignore" or "fail".
   */
  exception?: string,
  /**
   * The name of the data source (the scanner). If not set, the default data source is used.
   */
  scanner?: string,
  ui?: {
    /**
     * Whether to show the UI of the device.
     */
    bShowUI?: boolean,
    /**
     * Whether to show the indicator of the device.
     */
    bShowIndicator?: boolean,
  },
  /**
   * The TWAIN transfer mode.
   */
  transferMode?: Dynamsoft.EnumDWT_TransferMode | number,
  /**
   * Set how the transfer is done.
   */
  fileXfer?: {
    /**
     * Specify the file name (or pattern) for file transfer.
     * Example: "C:\\WebTWAIN<%06d>.bmp"
     */
    fileName?: string,
    /**
     * Specify the file format.
     */
    fileFormat?: Dynamsoft.EnumDWT_FileFormat | number,
    /**
     * Specify the quality of JPEG files.
     */
    jpegQuality?: number,
    /**
     * Specify the compression type of the file.
     */
    compressionType?: Dynamsoft.EnumDWT_CompressionType | number
  }
  /**
   * Set where the scanned images are inserted.
   */
  insertingIndex?: number,
  /**
   * The profile is a base64 string, if present, it overrides settings and more settings.
   */
  profile?: string,
  /**
   * Basic settings.
   */
  settings?: {
    /**
     * "ignore" (default) or "fail".
     */
    exception?: string,
    /**
     * Specify the pixel type.
     */
    pixelType?: Dynamsoft.EnumDWT_PixelType | number,
    /**
     * Specify the resolution.
     */
    resolution?: number,
    /**
     * Whether to enable document feader.
     */
    bFeeder?: boolean,
    /**
     * Whether to enable duplex scan.
     */
    bDuplex?: boolean
  },
  moreSettings?: {
    /**
     * "ignore" (default) or "fail".
     */
    exception?: string,
    /**
     * Specify the bit depth.
     */
    bitDepth?: number,
    /**
     * Specify the page size.
     */
    pageSize?: Dynamsoft.EnumDWT_CapSupportedSizes | number,
    /**
     * Specify the unit.
     */
    unit?: Dynamsoft.EnumDWT_UnitType | number,
    /**
     * Specify a layout to scan, if present, it'll override pageSize.
     */
    layout?: {
      left?: number,
      top?: number,
      right?: number,
      bottom?: number
    },
    /**
     * Specify the pixel flavor.
     */
    pixelFlavor?: Dynamsoft.EnumDWT_CapPixelFlavor | number,
    /**
     * Specify Brightness.
     */
    brightness?: number,
    /**
     * Specify contrast.
     */
    contrast?: number,
    /**
     * Specify how many images are transferred per session.
     */
    nXferCount?: number,
    /**
     * Whether to enable automatic blank image detection and removal.
     */
    autoDiscardBlankPages?: boolean,
    /**
     * Whether to enable automatic border detection.
     */
    autoBorderDetection?: boolean,
    /**
     * Whether to enable automatic skew correction.
     */
    autoDeskew?: boolean,
    /**
     * Whether to enable automatic brightness adjustment.
     */
    autoBright?: boolean
  },
  /**
   * A callback triggered before the scan, after the scan and after each page has been transferred.
   */
  funcScanStatus?: (status: Status) => void,
  /**
   * Set up how the scanned images are outputted.
   */
  outputSetup?: {
    /**
     * Output type. "http" is the only supported type for now.
     */
    type?: string,
    /**
     * Set the output format.
     */
    format?: Dynamsoft.EnumDWT_ImageType | number,
    /**
     * Specify how many times the library will try the output.
     */
    reTries?: 3,
    /**
     * Whether to use the FileUploader.
     */
    useUploader?: false,
    /**
     * Whether to upload all images in one HTTP post.
     */
    singlePost?: boolean,
    /**
     * Whether to show a progress bar when outputting.
     */
    showProgressBar?: boolean,
    /**
     * Whether to remove the images after outputting.
     */
    removeAfterOutput?: boolean,
    /**
     * A callback triggered during the outputting.
     * @argument fileInfo A JSON object that contains the fileName, percentage, statusCode, responseString, etc.
     */
    funcHttpUploadStatus?: (fileInfo: any) => void,
    /**
     * Setup for PDF output.
     */
    pdfSetup?: {
      author?: string,
      compression?: Dynamsoft.EnumDWT_PDFCompressionType | number,
      creator?: string,
      /**
       * Example: 'D:20181231'
       */
      creationDate?: string,
      keyWords?: string,
      /**
       * Example: 'D:20181231'
       */
      modifiedDate?: string,
      producer?: string,
      subject?: string,
      title?: string,
      version?: number,
      quality?: number
    },
    /**
     * Setup for TIFF output.
     */
    tiffSetup?: {
      quality?: number,
      compression?: Dynamsoft.EnumDWT_TIFFCompressionType | number,
      /**
       * Specify Tiff custom tags.
       */
      tiffTags?: TiffTag[]
    },
    /**
     * Setup for HTTP upload via Post.
     */
    httpParams?: {
      /**
       * Target of the request.
       * Example: "http://dynamsoft.com/receivepost.aspx"
       */
      url?: string,
      /**
       * Custom headers in the form.
       * Example: {md5: ""}
       */
      headers?: any,
      /**
       * Custom form fields.
       * Example: {"UploadedBy": "Dynamsoft"}
       */
      formFields?: any,
      /**
       * The maximum size of a file to be uploaded (in bytes).
       */
      maxSizeLimit?: number,
      /**
       * Specify how many threads (<=4) are to be used. Only valid when {useUploader} is true.
       */
      threads?: number,
      /**
       * Specify the names for the files in the form.
       * Example: "RemoteName<%06d>"
       */
      remoteName?: string,
      /**
       * Specify the name(s) (pattern) of the uploaded files.
       * Example: "uploadedFile<%06d>.jpg"
       */
      fileName?: string
    }
  }
}
```

---

## CancelAllPendingTransfers

**Syntax**

``` typescript
/**
 * Cancels all pending transfers.
 */ 
CancelAllPendingTransfers(): boolean;
```

**Usage notes**

This method is only valid in the events [OnPreAllTransfers](#onprealltransfers), [OnPreTransfer](#onpretransfer) and [OnPostTransfer](#onposttransfer).

---

## CloseSourceManager

**Syntax**

``` typescript
/**
 * Closes and unloads Data Source Manager.
 */
CloseSourceManager(): boolean;
```

---

## CloseSourceManagerAsync

**Syntax**

``` typescript
/**
 * Closes and unloads Data Source Manager.
 */
CloseSourceManagerAsync(): Promise<boolean>;
```

---

## CloseWorkingProcess

**Syntax**

``` typescript
/**
 * Closes the scanning process to release resources on the machine.
 */
CloseWorkingProcess(): boolean;
```

**Usage notes**

In the HTML5 edition, Dynamic Web TWAIN uses a separate process to communicate with the scanners. When it's not scanning, you can choose to close this process to release the resources (CPU, memory, etc.) used on the machine.

---

## FeedPage

**Syntax**

``` typescript
/**
 * Ejects the current page and begins scanning the next page in the document feeder.
 */
FeedPage(): boolean;
```

**Usage notes**

Use this method after [OpenSource()](#opensource) is called and make sure [IfFeederEnabled](#iffeederenabled) is `true` .

---

## GetCustomDSData

**Syntax**

``` typescript
/**
 * Get the custom data source data and saves the data in a specified file.
 * @param fileName The path of the file to save the data source data to.
 */
GetCustomDSData(fileName: string): boolean;
```

**Example**

``` javascript
DWObject.GetCustomDSData("C:\\customDSData");
```

---

## GetCustomDSDataEx

**Syntax**

``` typescript
/**
 * Gets custom DS data and returns it in a base64 string.
 */
GetCustomDSDataEx(): string;
```

---

## GetDeviceType

**Syntax**

``` typescript
/**
 * Inspect the current data source and return whether it is a scanner, a webcam, etc.
 */
GetDeviceType(): number;
```

**Usage notes**

| Value | Description |
|:-|:-|
| 0 | Failed |
| 1 | Digital Camera |
| 2 | Flatbed-only scanner |
| 3 | Flatbed, feeder, auto feed |
| 4 | Feeder-only scanner, auto feed |
| 5 | Flatbed, feeder, without auto feed |
| 6 | Feeder-only scanner, without auto feed |
| 7 | Webcam |

---

## GetSourceNameItems

**Syntax**

``` typescript
/**
 * Get the name of a data source by its index in data source manager source list.
 * @param index The index of the data source.
 */
GetSourceNameItems(index: number): string;
```

---

## OpenSourceManager

**Syntax**

``` typescript
/**
 * Load and open data source manager.
 */
OpenSourceManager(): boolean;
```

**Usage notes**

If application identification needs to be set, it should be set before this API.

---

## OpenSourceManagerAsync

**Syntax**

``` typescript
/**
 * Load and open data source manager.
 */
OpenSourceManagerAsync(): Promise<boolean>;
```

**Usage notes**

If application identification needs to be set, it should be set before this API.

---

## ResetImageLayout

**Syntax**

``` typescript
/**
 * Reset the image layout in the data source.
 */
ResetImageLayout(): boolean;
```

**Usage notes**

To set the image layout manually, you can use [SetImageLayout()](#setimagelayout)

---

## RewindPage

**Syntax**

``` typescript
/**
 * If called while {IfFeederEnabled} property is true, the data source will return the current page to the input area and return the last page from the output area into the acquisition area.
 */
RewindPage(): boolean;
```

**Usage notes**

Use this method after [OpenSource()](#opensource) method and make sure [IfFeederEnabled](#iffeederenabled) is `true` .

---

## SetCustomDSData

**Syntax**

``` typescript
/**
 * Sets custom data source data to be used for scanning, the data is stored in a file which can be regarded as a scanning profile.
 * @param fileName The path  of the file.
 */
SetCustomDSData(fileName: string): boolean;
```

**Usage notes**

Typically, the data source data file is created by the method [GetCustomDSData()](#getcustomdsdata).

---

## SetCustomDSDataEx

**Syntax**

``` typescript
/**
 * Set custom data source data to be used for scanning, the input is a base64 string.
 * @param dsDataString The string that contains custom data source data.
 */
SetCustomDSDataEx(dsDataString: string): boolean;
```

**Usage notes**

Typically the data source data string is created by the method [GetCustomDSDataEx()](#getcustomdsdataex)

---

## SetFileXferInfo

**Syntax**

``` typescript
/**
 * Set the file transfer information to be used in File Transfer mode.
 * @param fileName The path to transfer the file to.
 * @param fileFormat The format of the file.
 */
SetFileXferInfo(
    fileName: string,
    fileFormat: Dynamsoft.EnumDWT_FileFormat | number
): boolean;
```

**Usage notes**

Make sure the format you set is supported by the data source.

Example argument for the parameter `fileName`
* "C:\\webtwain.jpg": The next scanned image will be compressed as a JPEG file named `webtwain` and transferred to "C:\\".
* "C:\\webtwain" + <> + ".jpg": The scanned images will result in "C:\\webtwain1.jpg", "C:\\webtwain2.jpg", "C:\\webtwain3.jpg", etc.
* "C:\\webtwain" + <%06d> + ".jpg": The scanned images will result in "C:\\webtwain000001.jpg", "C:\\webtwain000002.jpg", "C:\\webtwain000003.jpg", etc.

Check out the available formats [Dynamsoft. EnumDWT_FileFormat]({{site.info}}api/Dynamsoft_Enum.html#dynamsoftenumdwt_fileformat).

**Example**

``` javascript
DWObject.OpenSource();
DWObject.TransferMode = Dynamsoft.EnumDWT_TransferMode.TWSX_FILE;
if (DWObject.TransferMode === Dynamsoft.EnumDWT_TransferMode.TWSX_FILE) {
    if (DWObject.SetFileXferInfo(
            "C:\\Temp\\WebTWAIN&lt;&gt;.bmp",
            EnumDWT_FileFormat.TWFF_BMP
        )) {
        DWObject.IfShowUI = true;
        DWObject.AcquireImage();
    }
}
```

---

## SetImageLayout

**Syntax**

``` typescript
/**
 * Set the left, top, right, and bottom sides of the image layout rectangle for the current data source. The image layout rectangle defines a frame of the data source's scanning area to be acquired.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param right Specify the rectangle (rightmost coordinate).
 * @param bottom Specify the rectangle (bottommost coordinate).
 */
SetImageLayout(
    left: number,
    top: number,
    right: number,
    bottom: number
): boolean;
```

**Usage notes**

The arguments set to the parameters `left` , `top` , `right` , `bottom` are based on the value of the `Unit` property which is `inches` by default.

This API is device-dependent. If a data source doesn't support the customization of the scan area, this method might not work correctly.

Since there are several ways to negotiate the scan area, it becomes confusing when deciding what should take precedence. 

The TWAIN Working Group has suggested the following behavior

* If the current frame is set by `SetImageLayout` . The same frame shall be what you get with the APIs [CapGetFrameBottom()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameBottom), [CapGetFrameLeft()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameLeft), [CapGetFrameRight()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameRight), [CapGetFrameTop()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameTop) and the property [PageSize](#pagesize) shall return `TWSS_NONE` | 0.
* If the current frame is set from negotiating the capability `ICAP_FRAMES` with the method [CapSetFrame()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapSetFrame), the property [PageSize](#pagesize) shall return `TWSS_NONE` | 0 and the image layout shall reflect the same frame with the properties [ImageLayoutFrameBottom](#imagelayoutframebottom), [ImageLayoutFrameLeft](#imagelayoutframeleft), [ImageLayoutFrameRight](#imagelayoutframeright) and [ImageLayoutFrameTop](#imagelayoutframetop).
* If the current fixed frame is set by the property [PageSize](#pagesize), the same dimensions shall be reflected in the APIs [CapGetFrameBottom()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameBottom), [CapGetFrameLeft()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameLeft), [CapGetFrameRight()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameRight), [CapGetFrameTop()](https://www.dynamsoft.com/docs/dwt15.3.1/API/Capability-Negotiation.html#CapGetFrameTop) as well as [ImageLayoutFrameBottom](#imagelayoutframebottom), [ImageLayoutFrameLeft](#imagelayoutframeleft), [ImageLayoutFrameRight](#imagelayoutframeright) and [ImageLayoutFrameTop](#imagelayoutframetop). Note, however, the orientation (in other words, whether it's in the portrait mole or landscape mode) also plays a role in the order of the values.

**Example**

``` javascript
DWObject.SelectSource();
DWObject.OpenSource();
DWObject.IfShowUI = false;
DWObject.Unit = Dynamsoft.EnumDWT_UnitType.TWUN_PIXELS;
DWObject.SetImageLayout(50, 50, 100, 100);
DWObject.AcquireImage();
```

---

## BitDepth

**Syntax**

``` 
/**
 * Return or set the pixel bit depth for the current value of `PixelType` .
 */
BitDepth: number;
```

**Usage notes**

Set this property after `OpenSource()` and before `AcquireImage()` .

By default, the bit depth is 1 for `TWPT_BW` , 8 for `TWPT_GRAY` and 24 for `TWPT_RGB` .

---

## IfAppendImage

**Syntax**

``` 
/**
 * Return or set whether newly acquired images are inserted or appended.
 */
IfAppendImage: boolean;
```

**Usage notes**

The value of this property defaults to `true` , which means that the newly acquired image will be appended to the last image in the buffer.

If it's set to `false` , the images will be inserted before the current image. The important thing to note is that, by design, the current image is always the last acquired one which means that the images acquired after setting `IfAppendImage` to `false` will be displayed / retained in the reverse order.

---

## IfDisableSourceAfterAcquire

**Syntax**

``` 
/**
 * Return or set whether to close the user interface after all images have been acquired.
 */
IfDisableSourceAfterAcquire: boolean;
```

**Usage notes**

This property only makes sense when `IfShowUI` is set to `true` .

---

## IfDuplexEnabled

**Syntax**

``` 
/**
 * Return or set whether to enable duplex scanning (in other words, whether to scan both sides of the paper).
 */
IfDuplexEnabled: boolean;
```

**Usage notes**

Set this property after `OpenSource()` and before `AcquireImage()` . 

Not all scanners support duplex scanning. To confirm, check the user manual of the device or check the value of `Duplex` after `OpenSource()` .

---

## IfFeederEnabled

**Syntax**

``` 
/**
 * Return or set whether a data source's Automatic Document Feeder (ADF) is enabled for scanning.
 */
IfFeederEnabled: boolean;
```

## Usage notes

Set this property after `OpenSource()` and before `AcquireImage()` .

If the property is set to `true` , the data source will try acquiring images from the document feeder first. If the data source doesn't have a document feeder, the flatbed will be used.

---

## IfShowUI

**Syntax**

``` 
/**
 * Return or set whether the data source displays the user interface when scanning.
 */
IfShowUI: boolean;
```

**Usage notes**

If the property is set to `true` , the data source will display its user interface when `AcquireImage()` is called. Otherwise, the UI will not be displayed and the scan will start immediately.

---

## ImageCaptureDriverType

**Syntax**

``` 
/**
 * Return or set the driver type which determines the type of sources to use.
 */
ImageCaptureDriverType: Dynamsoft.EnumDWT_Driver | number;
```

**Usage notes**

Set this property right after the SDK is initialized or after calling `CloseSourceManager()` and `OpenSourceManager()` .

The allowed values for `EnumDWT_Driver` are

| Label | Value | Description |
|:-|:-|:-|
| TWAIN | 0 | Use data sources that conforms to the TWAIN protocol |
| ICA | 3 | Use data sources that conforms to the Image Capture Architecture |
| SANE | 3 | Use data sources that conforms to the SANE API |
| TWAIN_AND_ICA | 4 | Use both TWAIN and ICA data sources |
| TWAIN_AND_TWAIN64 | 4 | Use both 32bit and 64bit TWAIN drivers |
| TWAIN64 | 5 | Use 64bit TWAIN sources |

---

## PageSize

**Syntax**

``` typescript
/**
 * Return or set the page size the data source uses to acquire images.
 */
PageSize: Dynamsoft.EnumDWT_CapSupportedSizes | number;
```

---

## PixelType

**Syntax**

``` typescript
/**
 * Return or set the pixel type used when acquiring images. 
 */
PixelType: Dynamsoft.EnumDWT_PixelType | number;
```

---

## Resolution

**Syntax**

``` typescript
/**
 * Return or set the resolution used when acquiring images.
 */
Resolution: number;
```

---

## SourceCount

**Syntax**

``` typescript
/**
 * Returns how many data sources are available on the local system.
 */
readonly SourceCount: number;
```

---

## BlankImageThreshold

**Syntax**

``` typescript
/**
 * Retrun or set the dividing line between black and white.
 */
BlankImageThreshold: number;
```

**Usage Notes**

`BlankImageThreshold` ranges from 0 to 255 and is 128 by default, it's only effective when [ `PixelType` ] is set to `TWPT_BW` . The bigger the value is, the more likely an image may be regarded as blank.

---

## Brightness

**Syntax**

``` typescript
/**
 * Return or set the brightness to be used for scanning by the data source.
 */
Brightness: number;
```

**Usage notes**

Set this property after `OpenSource()` and before `AcquireImage()` .

Typically, the value range is -1000 ~ 1000 where -1000 indicates the darkest and 1000 the brightest.

---

## Contrast

**Syntax**

``` typescript
/**
 * Return or set Contrast to be used for scanning by the data source.
 */
Contrast: number;
```

**Usage notes**

Set this property after `OpenSource()` and before `AcquireImage()` .

Typically, the value range is -1000 ~ 1000 where -1000 indicates the darkest and 1000 the brightest.

---

## CurrentSourceName

**Syntax**

``` typescript
/**
 * Return the device name of current source. 
 */
readonly CurrentSourceName: string; 
```

**Usage notes**

If no source is currently selected, this property returns "".

---

## DataSourceStatus

**Syntax**

``` typescript
/**
 * Return a value that indicates the data source status.
 */
DataSourceStatus: number;
```

**Usage notes**

| Value | Description|
|:-|:-|
| 0 | The data source is closed. |
| 1	| The data source is opened. |
| 2	| The data source is enabled. |
| 3	| The data source is acquiring images. |

---

## DefaultSourceName

**Syntax**

``` typescript
/**
 * Return the name of the default source.
 */
DefaultSourceName: string;
```

---

## Duplex

**Syntax**

``` typescript
/**
 * Return whether the source supports duplex. If yes, it further returns the level of duplex the data source supports.
 */
readonly Duplex: Dynamsoft.EnumDWT_DUPLEX | number;
```

**Usage notes**

| Label | Value | Description |
|:-|:-|:-|
| TWDX_NONE | 0 | duplex is not supported |
| TWDX_1PASSDUPLEX | 1 | 1-pass duplex |
| TWDX_2PASSDUPLEX | 2 | 2-pass duplex |

1-pass means the paper gets scanned on both sides at the same time. 2-pass means the paper passes the light bar twice to get both sides scanned separately.

---

## IfAutoBright

**Syntax**

``` typescript
/**
 * Return or set whether to enable the data source's auto-brightness feature.
 */
IfAutoBright: boolean;
```

---

## IfAutoDiscardBlankpages

**Syntax**

``` typescript
/**
 * Return or set whether the data source (the scanner) discards blank images during scanning automatically.
 */
IfAutoDiscardBlankpages: boolean;
```

**Usage notes**

The property works only if the device and its driver supports discarding blank pages. You can find whether your device supports this capbility from its user manual.

Alternatively, the Dynamic Web TWAIN library can also detect blank images after they are transferred.

---

## IfAutoFeed

**Syntax**

``` typescript
/**
 * Return or set whether to enable the data source's automatic document feeding process.
 */
IfAutoFeed: boolean;
```

**Usage notes**

If set to `true` , the data source will automatically feed the next page from the document feeder as soon as the previous page is scanned.

---

## IfAutomaticBorderDetection

**Syntax**

``` typescript
/**
 * Return or set whether to enable the data source's automatic border detection feature.
 */
IfAutomaticBorderDetection: boolean;
```

**Usage notes**

The property works only if the device and its driver support detecting the border automatically. You can find whether your device supports this capbility from its user manual.

Once enabled, the data source (scanner) will automatically detect the borders of the document so that no extra margins are scanned.

---

## IfAutomaticDeskew

**Syntax**

``` typescript
/**
 * Return or set whether to enable the data source's automatic skew correction feature.
 */
IfAutomaticDeskew: boolean;
```

**Usage notes**

The property works only if the device and its driver supports automatical deskewing. You can find whether your device supports this capbility from its user manual.

---

## IfAutoScan

**Syntax**

``` typescript
/**
 * Return or set whether to enable the data source's automatic document scanning process.
 */
IfAutoScan: boolean;
```

**Usage notes**

This property is only valid when [IfFeederEnabled](#iffeederenabled) is set to `true` .

The fundamental assumption behind this property is that the device may be able to capture the number of images indicated by the property [XferCount](#xfercount) without waiting for the Application to request the image transfers. This is
only possible if the device has internal buffers capable of caching the images it captures.

---

## IfFeederLoaded

**Syntax**

``` typescript
/**
 * Return whether or not there are documents loaded in the data source's feeder.
 */
readonly IfFeederLoaded: boolean;
```

**Usage notes**

This property is only valid when [IfFeederEnabled](#iffeederenabled) and [IfPaperDetectable](#ifpaperdetectable) are `true` .

---

## IfPaperDetectable

**Syntax**

``` typescript
/**
 * Return whether the Source has a paper sensor that can detect pages on the ADF or Flatbed.
 */
readonly IfPaperDetectable: boolean;
```

**Usage notes**

Check this property after [OpenSource()](#opensource) is called.

---

## IfShowIndicator

**Syntax**

``` typescript
/**
 * Return or set whether the data source displays a progress indicator during acquisition and transfer.
 */
IfShowIndicator: boolean;
```

**Usage notes**

This property works only when IfShowUI is set to `false` .

The indicator will only be hidden if you set both [IfShowUI](#ifshowui) and [IfShowIndicator](#ifshowindicator) to `false` .

---

## IfUIControllable

**Syntax**

``` typescript
/**
 * Return whether the data source supports acquisitions with the UI (User Interface) disabled.
 */
readonly IfUIControllable: boolean; 
```

**Usage notes**

Check this property after [OpenSource()](#opensource) is called.

---

## IfUseTwainDSM

**Syntax**

``` typescript
/**
 * Return or set whether the new TWAIN DSM (data source Manager) is used for acquisitions. The new TWAIN DSM is a DLL called 'TWAINDSM.dll' while the default | old DSM is called 'twain_32.dll'.
 */
IfUseTwainDSM: boolean;
```

**Usage notes**

This property should be set before any TWAIN related methods or properties are called or set.

---

## ImageLayoutFrameBottom

**Syntax**

``` typescript
/**
 * Return the value of the bottom edge of the current image frame (in Unit).
 */
readonly ImageLayoutFrameBottom: number;
```

---

## ImageLayoutFrameLeft

**Syntax**

``` typescript
/**
 * Return the value of the left edge of the current image frame (in Unit).
 */
readonly ImageLayoutFrameLeft: number;
```

---

## ImageLayoutFrameRight

**Syntax**

``` typescript
/**
 * Return the value of the right edge of the current image frame (in Unit).
 */
readonly ImageLayoutFrameRight: number;
```

---

## ImageLayoutFrameTop

**Syntax**

``` typescript
/**
 * Return the value of the top edge of the current image frame (in Unit).
 */
readonly ImageLayoutFrameTop: number;
```

---

## ImageLayoutDocumentNumber

**Syntax**

``` typescript
/**
 * Return the document number of the current image.
 */
readonly ImageLayoutDocumentNumber: number;
```

---

## ImageLayoutPageNumber

**Syntax**

``` typescript
/**
 * Return the page number of the current image.
 */
readonly ImageLayoutPageNumber: number;
```

---

## ImageBitsPerPixel

**Syntax**

``` typescript
/**
 * Return the bit depth of the current image.
 */
readonly ImageBitsPerPixel: number;
```

---

## ImageLength

**Syntax**

``` typescript
/**
 * Return the length of the current image.
 */
readonly ImageLength: number;
```

---

## ImageWidth

**Syntax**

``` typescript
/**
 * Return the width of the current image.
 */
readonly ImageWidth: number;
```

---

## ImageXResolution

**Syntax**

``` typescript
/**
 * Return the horizontal resolution of the current image.
 */
readonly ImageXResolution: number;
```

---

## ImageYResolution

**Syntax**

``` typescript
/**
 * Return the vertical resolution of the current image.
 */
readonly ImageYResolution: number;
```

---

## ImagePixelType

**Syntax**

``` typescript
/**
 * Return the pixel type of the current image.
 */
readonly ImagePixelType: Dynamsoft.EnumDWT_PixelType | number;
```

---

## MagData

**Syntax**

``` typescript
/**
 * Return the data of the magnetic data if the data source supports magnetic data recognition.
 */
readonly MagData: string;
```

---

## MagType

**Syntax**

``` typescript
/**
 * Return the type of the magnetic data if the data source supports magnetic data recognition.
 */
readonly MagType: Dynamsoft.EnumDWT_MagType | number;
```

**Usage notes**

The numbers returned by these APIs are based on the value of the [Unit](#unit) property which by default means "inches".

These APIs are only valid in the callbacks for the events [OnPreTransfer](#onpretransfer) and [OnPostTransfer](#onposttransfer).

`MagData` and `MagType` are device-dependent. Check the user manual of the device to see if magnetic data recognition is supported.

---

## PendingXfers

**Syntax**

``` typescript
/**
 * Return the number of transfers the data source is ready to supply upon demand.
 */
readonly PendingXfers: number;
```

**Usage notes**

This property is only valid in the event [OnPostTransfer](#onposttransfer).

The data source returns -1 if it is not sure how many transfers are pending which normally occurs when the ADF (Automatic Document Feeder) is used.

---

## PixelFlavor

**Syntax**

``` typescript
/**
 * Return or set the pixel flavor to be used for acquiring images.
 */
PixelFlavor: number;
```

**Usage notes**

Available values: 

* 0: Chocolate. Zero pixel represents darkest shade
* 1: Vanilla. Zero pixel represents lightest shade.

---

## TransferMode

**Syntax**

``` typescript
/**
 * Return or set the data source's transfer mode.
 */
TransferMode: Dynamsoft.EnumDWT_TransferMode | number;
```

**Usage notes**

Allowed values are

* TWSX_NATIVE | 0: The default mode. In this mode, the whole image is transfered in a single memory block. 
* TWSX_FILE | 1: In this mode, the image is transfered to a specified file on the disk directly. This mode is ideal when transferring large images that might encounter memory limitations with Native mode. Check out [SetFileXferInfo](#SetFileXferInfo) for more information.
* TWSX_MEMORY | 2: In this mode, the image is transferred in multiple memory blocks. It's ideal for transferring very large images or a large number of images in a short time.

TWSX_NATIVE and TWSX_MEMORY are required by all TWAIN data sources while TWSX_FILE is not. Therefore, make sure the data source supports TWSX_FILE before you use it.

---

## Unit

**Syntax**

``` typescript
/**
 * Return or set the unit of measure for all quantities.     
 */
Unit: Dynamsoft.EnumDWT_UnitType | number;
```

**Usage notes**

Allowed values are

| Label | Value | Description |
|:-|:-|:-|
| TWUN_INCHES | 0 | inches(Default)
| TWUN_CENTIMETERS | 1 |centimeters |
| TWUN_PICAS | 2 | picas |
| TWUN_POINTS | 3 | points |
| TWUN_TWIPS | 4 | twips |
| TWUN_PIXELS | 5 | pixels |
| TWUN_MILLIMETERS | 6 | millimeters |

---

## XferCount

**Syntax**

``` typescript
/**
 * Return and set the number of images your application is willing to accept for each scan job.
 */ 
XferCount: number;
```

**Usage notes**

Allowed values are between -1 and 215 where -1 indicate multiple images.

---

## OnPostAllTransfers

**Syntax**

``` typescript
/**
 * This event is triggered when all page(s) have been scanned and transferred.
 */
RegisterEvent('OnPostAllTransfers',function(){});
```

**Usage notes**

This event fires after all pages in the document feeder have been scanned and transferred. This is a good place to upload the images, detect barcodes, discard blank pages, etc.

**Example**

``` javascript
DWObject.RegisterEvent('OnPostAllTransfers',
    function() {
        console.log("All images are transferred.");
    }
);
```

---

## OnPostTransfer

**Syntax**

``` typescript
/**
 * This event is triggered after each page has been scanned and transferred.
 * @argument outputInfo Detailed information about the image that just got transferred.
 */ 
RegisterEvent('OnPostTransfer',function(outputInfo: OutputInfo) {});
```

**Example**

``` javascript
DWObject.RegisterEvent('OnPostTransfer',
    function() {
        console.log("An image has been scanned");
    }
);
```

---

## OnPostTransferAsync

**Syntax**

``` typescript
/**
 * This event is triggered after each page has been scanned and transferred. This is the asynchronous counterpart to the synchronous event {OnPostTransfer}.
 * @argument outputInfo Detailed information about the image that just got transferred.
 */ 
RegisterEvent('OnPostTransferAsync',function(outputInfo: OutputInfo) {});
```

**Usage notes**

``` typescript
interface outputInfo {
    /**
     * Id of the image if it's transferred to the buffer.
     */
    imageId?: number;
    /**
     * Path of the image if it's transferred to the disk.
     */
    Path?: string;
    /**
     * Information about the image.
     */
    imageInfo?: object;
    /**
     * Extended information about the image.
     */
    extendedImageInfo?: object;
}
```

**Example**

``` javascript
DWObject.RegisterEvent('OnPostTransferAsync',
    function(outputInfo) {
        console.log("The image ID is " + outputInfo.imageId);
    }
);
```

---

## OnPreAllTransfers

**Syntax**

``` typescript
/**
 * This event is triggered when all images are scanned and ready to be transferred.
 */
RegisterEvent('OnPreAllTransfers',function(){});
```

**Usage notes**

Multiple transfers may occur in two cases

* Multiple images are scanned through the ADF(Auto Document Feeder)
* Multiple frames are scanned on one single page

In such cases, the event `OnPreTransfer` is triggered multiple times but `OnPreAllTransfers` is triggerred only once. 

In the callback function of this event, you can call `CancelAllPendingTransfers()` to cancel all the transfers.

---

## OnPreTransfer

**Syntax**

``` typescript
/**
 * This event is triggered when a page has been scanned and is ready to be transferred.
 */
RegisterEvent('OnPreTransfer',function(){...});
```

**Usage notes**

In the callback function of this event, you can 

* Check `PendingXFERs` for the number of pending transfers. 
* Check the information about the transferred image including `ImageLayoutDocumentNumber` , `ImageLayoutFrameLeft` , `ImageLayoutFrameTop` , `ImageLayoutFrameRight` , `ImageLayoutFrameBottom` , `ImageLayoutPageNumber` , `ImageLayoutFrameNumber` , etc.
* Call `CancelAllPendingTransfers()` to cancel all the rest of the transfers.

---

## OnSourceUIClose

**Syntax**

``` typescript
/**
 * This event is triggered when the user interface of the data source is closed manually by the user.
 */
RegisterEvent('OnSourceUIClose',function() {});
```

---

## getCapabilities

**Syntax**

``` typescript
/**
 * Gets detailed information about all capabilities of the current data source.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument capabilityDetails Detailed information about the specified capabilities.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
getCapabilities(
    successCallback: (capabilityDetails: CapabilityDetails[]) => void,
    failureCallback: (
        errorCode: number,
        errorString: string
    ) => void
): void;

/**
 * Detailed information about a specific capability
 */
interface CapabilityDetails {
    /**
     * The Capability.
     */
    capability: ValueAndLabel;
    /**
     * The container type of the Capability
     */
    conType: ValueAndLabel;
    /**
     * The index for the current value of the Capability
     */
    curIndex: number;
    /**
     * The current value of the Capability
     */    
    curValue: ValueAndLabel;
    /**
     * The index for the default value of the Capability
     */    
    defIndex: number;
    /**
     * The operation types that are supported by the Capability. Types include {"get", "set", "reset" "getdefault", "getcurrent"}
     */   
    query: string[];
    /**
     * The value type of the Capability. Value types include
        TWTY_BOOL: 6
        TWTY_FIX32: 7
        TWTY_FRAME: 8
        TWTY_INT8: 0
        TWTY_INT16: 1
        TWTY_INT32: 2
        TWTY_STR32: 9
        TWTY_STR64: 10
        TWTY_STR128: 11
        TWTY_STR255: 12
        TWTY_UINT8: 3
        TWTY_UINT16: 4
        TWTY_int: 5
     */    
    valueType: ValueAndLabel;
    /**
     * The available values of the Capability
     */    
    values: ValueAndLabel[];
}

interface ValueAndLabel {
    /**
     * Numeric representation of the item
     */
    value: Dynamsoft.EnumDWT_Cap | Dynamsoft.EnumDWT_CapType | Dynamsoft.EnumDWT_CapValueType | number;
    /**
     * Label or name of the item
     */    
    label: string;
}
```

**Usage notes**

Check out the Enumerations

* [ `Dynamsoft.EnumDWT_Cap` ]({{site.info}}api/Dynamsoft_Enum.html#enumdwt_cap)
* [ `Dynamsoft.EnumDWT_CapType` ]({{site.info}}api/Dynamsoft_Enum.html#enumdwt_captype)
* [ `Dynamsoft.EnumDWT_CapValueType` ]({{site.info}}api/Dynamsoft_Enum.html#enumdwt_capvaluetype)

---

## setCapabilities

**Syntax**

``` typescript
/**
 * Sets up one or multiple capabilities in one call.
 * @param capabilities A object that describes how to set capabilities.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument capabilities The capabilities to set.
 */
setCapabilities(
    capabilities: Capabilities,
    successCallback: (capabilities: Capabilities) => void,
    failureCallback: (capabilities: Capabilities) => void
): void;

interface Capabilities {
    /**
     * Whether to "ignore" or "fail" the request if an exception occurs. This is an overall setting that is inherited by all capabilities. 
     */
    exceptition: string;
    /**
     * Specifies how to set capabilities
     */
    capabilities: CapabilitySetup[]
}

interface CapabilitySetup {
    /**
     * Specify a capability
     */
    capability: Dynamsoft.EnumDWT_Cap | number;
    /**
     * The value to set to the capability or the value of the capability after setting.
     */
    curValue: number | string;
    errorCode?: number;
    errorString?: string;
    /**
     * Whether to "ignore" or "fail" the request if an exception occurs when setting this specific capability.
     */
    exception? : string;
}
```

**Usage notes**

To make things easier, Dynamsoft designed the API with a simplified parameter `Capabilities` which only requires the minimum information for setting a capability: a number to specify the capability and the value to set to it. Underneath, Dynamsoft takes care of container type setting, value type setting as well as data validation.

Pay attention to the argument you set to the overall parameter `exception` and the individual parameter `exception` for each capability. If the overall parameter is set to `fail` , the setting will abort as soon as an exception is raised while setting any of the capabilities. Otherwise, `ignore` means to carry on setting the next capability even when the previous one failed. Aside from the overall parameter, the individual `exception` is optional but takes precedence if set. In other words, you can set the overall `exception` to `ignore` and then set the individual one to `fail` for the capabilities which you think are important. This way, you get notified if these important capabilities failed to be set while other less-important ones are ignored when setting them failed.
