---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API Reference - Viewer APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Viewer APIs
breadcrumbText: Viewer
description: Dynamic Web TWAIN SDK Documentation API Reference Viewer APIs Page
---

# `WebTwain.Viewer`

**Methods**

* [bind()](#bind)
* [clearSelectedAreas()](#clearselectedareas)
* [createCustomElement()](#createcustomelement)
* [createImageEditor()](#createimageeditor)
* [createThumbnailViewer()](#createthumbnailviewer)
* [first()](#first)
* [fitWindow()](#fitwindow)
* [gotoPage()](#gotopage)
* [hide()](#hide)
* [last()](#last)
* [next()](#next)
* [off()](#off)
* [on()](#on)
* [previous()](#previous)
* [render()](#render)
* [setButtonClass()](#setbuttonclass)
* [setSelectedAreas()](#setselectedAreas)
* [setViewMode()](#setviewmode) 
* [show()](#show)
* [unbind()](#unbind)

**Properties**

* [acceptDrop](#acceptdrop)
* [allowSlide](#allowslide)
* [background](#background)
* [border](#border)
* [cursor](#cursor)
* [height](#height)
* [idPostfix](#idpostfix)
* [ifAutoScroll](#ifautoscroll)
* [innerBorder](#innerBorder)
* [pageMargin](#pagemargin)
* [selectedAreaBorderColor](#selectedareabordercolor)
* [selectedPageBackground](#selectedpagebackground)
* [selectedPageBorder](#selectedpageborder)
* [selectionRectAspectRatio](#selectionrectaspectratio)
* [showPageNumber](#showpagenumber)
* [singlePageMode](#singlepagemode)
* [width](#width)
* [zoom](#zoom)

**Events**

* [click](#click)
* [contextmenu](#contextmenu)
* [dblclick](#dblclick)
* [mousemove](#mousemove)
* [pageAreaSelected](#pageareaselected)
* [pageAreaUnselected](#pageareaunselected)
* [pageRendered](#pagerendered)
* [resize](#resize)
* [topPageChanged](#toppagechanged)

> The following APIs are deprecated as of v16.2, check out [Viewer related API changes in version 16.2]({{site.info}}api/appendix.html#viewer-related-api-changes-in-versoin-16.2).

**Methods**

* `BindViewer()`
* `UnbindView()`
* `UpdateViewer()`

**Properties**

* `BackgroundColor`
* `SelectionImageBorderColor`
* `FitWindowType`
* `IfFitWindow`
* `Height`
* `Width`
* `IfAutoScroll`
* `ShowPageNumber`
* `MouseX`
* `MouseY`
* `ImageMargin`
* `MouseShape`
* `SelectionRectAspectRatio`
* `Zoom`

**Events**

* `OnMouseClick`
* `OnMouseDoubleClick`
* `OnMouseMove`
* `OnMouseRightClick`
* `OnImageAreaSelected`
* `OnImageAreaDeSelected`

---


## bind

**Syntax**

``` typescript
/**
 * Create a Dynamsoft Viewer instance and bind it to the WebTwain instance.
 * @param element Specify an HTML element to create the viewer.
 */
bind(
  element: boolean;
)
```
**Example**

``` typescript
DWObject.Viewer.bind(document.getElementById("divCustomElement")); 

///Initialize the settings of the Viewer, such as width, background, thumbnail, etc. Then calling show to display the configured style you set///  

DWObject.Viewer.show(); 
```

**Usage notes**

Replace the previous `BindViewer` method.

## clearSelectedAreas

**Syntax**

``` typescript
/**
 * Clear the selected area(s) on the current image
 */
clearSelectedAreas(): void;
```
**Example**

``` typescript
DWObject.Viewer.clearSelectedAreas();  
```

## createCustomElement

**Syntax**

``` typescript
/**
 * Add a custom page DIV element and specify its position and display order, and return an object that can control this element.
 * Generate an independent CustomElement object. 
 * @param element HTMLDivElement is required.
 * @param location? Define where to place the custom element. The optional values are left and right, and the default value is right.
 * @param isFull The default value is false, that is, the created CustomElement is displayed according to the set area. If set to true, the main viewer will display all the contents of CustomElement, and the other contents of the main viewer will be covered below.
 */
createCustomElement(
    element: HTMLDivElement, 
    location?: string, 
    isFull: boolean = false
    ): CustomElement; 
```

**Example**

``` typescript
var myElement=document.createElement("div");
myElement.style="width:100px;height:200px;background:red;" //display the custom element 100x200 into the viewer 
var customElement = DWObject.Viewer.createCustomElement(myElement, "right", false);
customElement.show(); //call show to display the custom element you set
```

**Usage notes**

Only one CustomElement object can be created. If you create it a second time or more, you'll get 'A CustomElement already exists.' error, and an existing CustomElement object will be returned.

If the width defined by the CustomElement object exceeds the width of the main viewer, the width of the main viewer is taken.

When call unbind, all created CustomElement objects, ThumbnailViewer objects, and ImageEditor objects will be disposed. After rebinding the viewer, you need to recreate the CustomElement object, ThumbnailViewer object, and ImageEditor object.

## createImageEditor

**Syntax**

``` typescript
/** 
 * Generate an independent ImageEditor object.
 * @param editorSettings? the ImageEditor settings
 */
 createImageEditor(
     editorSettings?: EditorSettings
 ): ImageEditor;
```

**Example**

> The example code shows 2 ways to use the API `createImageEditor()`

``` typescript
var imageEditor = DWObject.Viewer.createImageEditor();
  imageEditor.show(); //call show to display the image editor

var editorSettings = {
    border: '1px solid rgb(204, 204, 204);',
    topMenuBorder: '',
    innerBorder: '',
    background: "rgb(255, 255, 255)",
    promptToSaveChange: true,
    buttons: {
        titles: {
            'previous': 'Previous Image',
            'next': 'Next Image',
            'print': 'Print Image',
            'scan': 'Scan Documents',
            'load': 'Load Local Images',
            'rotateleft': 'Rotate Left',
            'rotate': 'Rotate',
            'rotateright': 'Rotate Right',
            'deskew': 'Deskew',
            'crop': 'Crop Selected Area',
            'erase': 'Erase Selected Area',
            'changeimagesize': 'Change Image Size',
            'flip': 'Flip Image',
            'mirror': 'Mirror Image',
            'zoomin': 'Zoom In',
            'originalsize': 'Show Original Size',
            'zoomout': 'Zoom Out',
            'stretch': 'Stretch Mode',
            'fit': 'Fit Window',
            'fitw': 'Fit Horizontally',
            'fith': 'Fit Vertically',
            'hand': 'Hand Mode',
            'rectselect': 'Select Mode',
            'zoom': 'Click to Zoom In',
            'restore': 'Restore Original Image',
            'save': 'Save Changes',
            'close': 'Close the Editor',
            'removeall': 'Remove All Images',
            'removeselected': 'Remove All Selected Images'
        },
        visibility: {
            'scan': true, 'load': true, 'print': true,
            'removeall': true, 'removeselected': true,
            'rotateleft': true, 'rotate': true, 'rotateright': true, 'deskew': true,
            'crop': true, 'erase': true, 'changeimagesize': true, 'flip': true, 'mirror': true,
            'zoomin': true, 'originalsize': true, 'zoomout': true, 'stretch': true,
            'fit': true, 'fitw': true, 'fith': true,
            'hand': true, 'rectselect': true, 'zoom': true, 'restore': true, 'save': true, 'close': true
        }
    },
    dialogText: {
        dlgRotateAnyAngle: ['Angle :', 'Interpolation:', 'Keep size', '  OK  ', 'Cancel'],
        dlgChangeImageSize: ['New Height :', 'New Width :', 'Interpolation method:', '  OK  ', 'Cancel'],
        saveChangedImage: ['You have changed the image, do you want to keep the change(s)?', '  Yes  ', '  No  '],
        selectSource: ['Select Source:', 'Select', 'Cancel', 'There is no source available']
    }
};

var imageEditor = DWObject.Viewer.createImageEditor(editorSettings);
imageEditor.show(); 
```

**Usage notes**

Replace the previous `ShowImageEditor` method.

Only one ImageEditor object can be created. If you create it a second time or more, you'll get 'An ImageEditor already exists.' error, and an existing ImageEditor object will be returned.

When call unbind, all created CustomElement objects, ThumbnailViewer objects, and ImageEditor objects will be disposed. After rebinding the viewer, you need to recreate the CustomElement object, ThumbnailViewer object, and ImageEditor object.

## createThumbnailViewer

**Syntax**

``` typescript
/**
 * Generate a independent ThumbnailViewer object.
 * @param thumbnailViewerSettings? the thumbnailViewer settings
 */
 createThumbnailViewer(
     thumbnailViewerSettings?: thumbnailViewerSettings
 ):ThumbnailViewer;
```

**Example**

> The example code shows 2 ways to use the API `createThumbnailViewer()`

``` typescript
var objThumbnailViewer = DWObject.Viewer.createThumbnailViewer();  
objThumbnailViewer.show(); //call show to display the thumbnail viewer.

[Yesterday 5:21 PM] Ellie
    var thumbnailViewerSettings = {​​​​​​​
    location: 'left',
    size: '30%',
    columns: 1,
    rows: 3,
    scrollDirection: 'vertical',  // 'horizontal'
    margin: 10,
    background: "rgb(255, 255, 255)",
    border: '',
    allowKeyboardControl: true,
    allowPageDragging: true,
    allowResizing: false,
    showPageNumber: false,
    pageBackground: "transparent",
    pageBorder: "1px solid rgb(238, 238, 238)",
    hoverBackground: "rgb(239, 246, 253)",
    hoverBorder: "1px solid rgb(238, 238, 238)",
    placeholderBackground: "rgb(251, 236, 136)",
    selectedImageBorder: "1px solid rgb(125,162,206)",
    selectedImageBackground: "rgb(199, 222, 252)"
}​​​​​​​;

var thumbnail = DWObject.Viewer.createThumbnailViewer(thumbnailViewerSettings);
thumbnail.show();

```

**Usage notes**

Scrolling the scroll bar on Thumbnail does not trigger the topchanged event by default.

Only one ThumbnailViewer object can be created. If you create it a second time or more, you'll get 'A ThumbnailViewer already exists.' error, and an existing ThumbnailViewer object will be returned.

When call unbind, all created CustomElement objects, ThumbnailViewer objects, and ImageEditor objects will be disposed. After rebinding the viewer, you need to recreate the CustomElement object, ThumbnailViewer object, and ImageEditor object.

## first

**Syntax**

``` typescript
/** 
 * Return the index of the fist image.
 * If there is no image in the viewer, -1 is returned.
 */
first():number; 
```

**Example**

``` typescript
DWObject.Viewer.first(); 
```

## fitWindow

**Syntax**

``` typescript
/**
 * Set how the image is fit in the viewer.
 * @param type specify a type to fit 
 */
fitWindow(
    type: string
): void
```

**Example**

``` typescript
 DWObject.Viewer.fitWindow();  
```

**Usage notes**

This API only works if the view mode of the viewer is set to -1 by -1.

The allowed values of fitWindow are

No parameters: Default value, try to fit the image both horizontally and vertically.
width: Fit the image vertically.
height: Fit the image horizontally.

## gotoPage

**Syntax**

``` typescript
/**
 * Go to the image you specified.
 * @param index Specify the image.
 */
gotoPage(
    index: number
): number;
```

**Example**

``` typescript
DWObject.Viewer.gotoPage(0);
```

## hide

**Syntax**

``` typescript
/**
 * Hide the image editor.
 */
hide(): void;
```

**Example**

``` typescript
var objImageEditor = DWObject.Viewer.createImageEditor(editorSettings?: EditorSettings);  
objImageEditor.show(); 
```

## last

**Syntax**

``` typescript
/** 
 * Return the index of the last image.
 * If there is no image in the viewer, -1 is returned.
 */
last():number; 
```

**Example**

``` typescript
DWObject.Viewer.last(); 
```

## next

**Syntax**

``` typescript
/**
 * Return the index of the next image of the currently selected image.
 */
next(): number; 
```

**Example**

``` typescript
DWObject.SelectImages([3]); 
var currentIndex=DWObject.Viewer.next();// return 4
```

## off

**Syntax**

``` typescript
/**
 * Unbind the viewer event.
 * 
 */
Viewer.off(
    eventName: string, 
    callback?: () => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.off('pageAreaSelected');
```

## on

**Syntax**

``` typescript
/**
 * Bind the viewer event.
 * @param eventName The event name.
 */
Viewer.on(
    eventName: string, 
    callback: (event: ViewerEvent) => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.on('pageAreaSelected', function(sImageIndex, rect){console.log(sImageIndex)});
```

## previous

**Syntax**

``` typescript
/**
 * Return the index of the previous image of the currently selected image.
 * 
 */
previous(): number; 
```

**Example**

``` typescript
DWObject.SelectImages([3]); 
var currentIndex=DWObject.Viewer.previous();// return 2
```

## render

**Syntax**

``` typescript
/**
 * Refresh the viewer.
 */

render(): void; 
```

**Example**

``` typescript
DWObject.Viewer.on("pageRendered",function(index){
 console.log(index)
 });
 
DWObject.Viewer.render();  //it will trigger the pageRendered event
```

## setButtonClass

**Syntax**

``` typescript
/**
 * Set the CSS class name of the specified button defined in updateUISetting.
 * @param name Specify the button.
 * @param className Specify the CSS class name.
 */
setButtonClass(
    name: string,
    className: string
): boolean;
```

**Usage notes**

Use this method to fine-tune the buttons in updateUISetting with CSS.

**Example**

``` javascript
DWObject.Viewer.setButtonClass('crop', 'ds-dwt-ui-icon-cropImage-grey');  
```

## setSelectedAreas 

**Syntax**

``` typescript
/**
 * set one or more rectangular area on the specified image.
 * @param areas Specify the rectangle.
 */
setSelectedAreas(
    areas: Area[]
): void;

interface Area{}
    left: number,
    top: number,
    right: number,
    bottom: number,
);

```
**Usage notes**

The coordinates are based on the size of the original image (instead of the size of the viewer).

**Example**

``` typescript
DWObject.Viewer.setSelectedAreas([{left:0, top:0, right:100, bottom:100}],[{left:200, top:200, right:400, bottom:500}]); 
```

## setViewMode

**Syntax**

``` typescript
/**
 * Set the view mode of the viewer.
 * @param columns Specify the number of images per row.
 * @param rows Specify the number of images per column.
 */
setViewMode(
    columns: number,
    rows: number
): boolean;
```

**Example**

``` typescript
DWObject.Viewer.setViewMode(2, 2);  
```

## show

**Syntax**

``` typescript
/**
 * Show the viewer you created(ImageEditor, ThumbnailViewer, CustomElement).
 * 
 */
show(): void; 
```

**Example**

``` typescript
var objImageEditor = DWObject.Viewer.createImageEditor();  
objImageEditor.show(); 
```

## unbind

**Syntax**

``` typescript
/**
 * Unbind and destroy the viewer.
 */
unbindViewer(): boolean; 
```

**Example**

``` typescript
DWObject.Viewer.unbindViewer();  
```

**Usage notes**

Replace the previous `UnbindViewer` method.

## acceptDrop

**Syntax**

``` typescript
/**
 * Set whether to disable the drag and drop image to the viewer function.
 * The default value is true.
 */
acceptDrop: boolean; 
```

**Example**

``` typescript
DWObject.Viewer.acceptDrop = true;  
```

## background

**Syntax**

``` typescript
/**
 * Return or set the background colour of the viewer.
 */
background: string;
```

**Example**

``` typescript
DWObject.Viewer.background = 'rgb(255, 255, 255);';  
```

**Usage notes**

Replace the previous `BackgroundColor` method.

## border

**Syntax**

``` typescript
/**
 * Return or set the border of the viewer.
 * Defalut value is 1px solid rgb(204, 204, 204)
 */
border: string; 
```

**Example**

``` typescript
DWObject.Viewer.border = '2px solid rgb(204, 204, 204)'; 
```

## cursor

**Syntax**

``` typescript
/**
 * Return or set the shape of the cursor.
 */
cursor: string; 
```

**Usage notes**

The allowed values are:

| Value | Description |
|:-|:-|
| default | The shape is “arrow”.|
| crosshair (defalut value) | The shape is “crosshair”, you can drag to select an area on the image. |
| pointer | The shape is “hand”. Only works if the view mode of the viewer is set to -1 * -1, and the displayed image does not fit the Window (when there is a scroll bar), then the image can be moved.|
| zoom-in | The shape is “magnifier”, supports click the image to zoom in. Only works if the view mode of the viewer is set to -1 by -1.|

**Example**

``` typescript
DWObject.Viewer.cursor = 'crosshair';  
```

## height

**Syntax**

``` typescript
/**
 * Return or set the height of the viewer.
 */ 
height: number | string;
```

**Usage Notes**

If a number is assigned, it means that number of pixels (px). If a string is assigned, it is either a fixed size like "500px" or a dynamic size like "50%" which follows standard CSS rules.

**Example**

``` javascript
DWObject.Viewer.height = 350;
DWObject.Viewer.height = "350px";
DWObject.Viewer.height = "100%";
```

## idPostfix

**Syntax**

``` typescript
/**
 * Return the postfix of the Ids of the elements in the viewer.
 */ 
readonly Viewer.idPostfix: string;
```

**Example**

``` javascript
var myViewerIdPostfix = DWObject.Viewer.idPostfix;
```

## innerBorder

**Syntax**

``` typescript
/**
 * Return or set the inner border of the viewer.
 * Defalut value is 1px solid rgb(125,162,206)
 */
border: string; 
```

**Example**

``` typescript
DWObject.Viewer.innerBorder = '1px solid rgb(204, 204, 204)';  
```

## pageMargin

**Syntax**

``` typescript
/**
 * Return or set the margin between images.
 */
.pageMargin: number | string; 
```

**Usage Notes**

The page margin is only effective when the view mode is not -1 * -1.

**Example**

``` typescript
DWObject.Viewer.pageMargin = 10;  
```

## selectedAreaBorderColor

**Syntax**

``` typescript
/**
 * Set the border color of the selected area 
 * The default value is rgb(42, 29, 43)
 */
selectedAreaBorderColor: string; 
```

**Example**

``` typescript
DWObject.Viewer.selectedAreaBorderColor = 'rgb(255, 0, 0)';  
```

## selectedPageBackground

**Syntax**

``` typescript
/**
 * Set the selected page background color of the Thumbnail viewer.
 * Defalut value： rgb(199, 222, 252)
 */
selectedPageBackground: string; 
```

**Example**

``` typescript
DWObject.Viewer.selectedPageBackground = "rgb(255, 0, 0)";  
```

## selectedPageBorder

**Syntax**

``` typescript
/**
 * Return or set the border style for selected image(s).
 * Defalut value: 1px solid rgb(125,162,206)
 */
selectedPageBorder: string; 
```

**Example**

``` typescript
DWObject.Viewer.selectedPageBorder = "3px solid rgb(125,162,206)";  
```

**Usage Notes**

This API is only effective when the view mode is not -1 * -1.

## selectionRectAspectRatio

**Syntax**

``` typescript
/**
 * Specify a aspect ratio to be used when selecting a rectangle on an image.
 */
selectionRectAspectRatio: number | string; 
```

**Example**

``` typescript
DWObject.Viewer.selectionRectAspectRatio = 0.5;  
```

## showPageNumber

**Syntax**

``` typescript
/**
 * Return or set whether to show the page numbers.
 * The default value is false.
 */
```

**Example**

``` typescript
DWObject.Viewer.showPageNumber=true;
```

**Usage notes**

The page number indicates the order of the images.

When the viewmode is -1 * -1, page numbers will be hidden.

## singlePageMode

**Syntax**

``` typescript
/**
 * Set whether to use single page mode. 
 * The default value is false, that is, the view mode is 1 * 1. True means the view mode is -1 * -1.
 */
singlePageMode: boolean; 
```

**Example**

``` typescript
DWObject.Viewer.singlePageMode = true;  
```

## width

**Syntax**

``` typescript
/**
 * Return or set the width of the viewer.
 */ 
width: number | string;
```

**Usage Notes**

If a number is assigned, it means that number of pixels (px). If a string is assigned, it is either a fixed size like "500px" or a dynamic size like "50%" which follows standard CSS rules.
 
**Example**

``` javascript
DWObject.Viewer.width = 270;
DWObject.Viewer.width = "270px";
DWObject.Viewer.width = "100%";
```

## zoom

**Syntax**

``` typescript
/**
 * Return or set the zoom factor.
 * Allow value [0.02 ~ 65].
 */
zoom: number;
```

**Example**

``` typescript
DWObject.Viewer.zoom = 2.0;  
```

**Usage Notes**

The zoom factor is only effective when the view mode is -1 * -1.

When you set the property and the view mode is -1 * -1, the view will zoom in or out.

## click

## contextmenu

## dblclick

## mousemove

**Syntax**

``` typescript
/** 
 * A built-in callback triggered when the mouse click | right-click | double-click| on an image or move over it.
 * @param eventName The event name.
 * @argument index The index of the current image.
 */
Viewer.on(
    eventName: string, 
    callback: (event: ViewerEvent) => void
): void;

interface ViewerEvent{ 
   /** 
    * The index of the current image.
    */ 
    index: number; 
   /** 
    * The x-coordinate of the upper-left corner of the image.
    */ 
    imageX: number; 
    /** 
     * The y-coordinate of the upper-left corner of the image.
     */ 
    imageY: number; 
   /** 
    * The x-coordinate of the browser page.
    */ 
     pageX: number; 
   /** 
    * The y-coordinate of the browser page.
    */ 
     pageY: number; 
} 
```

**Example**

``` typescript
DWObject.Viewer.on('click',function(index){
 console.log(index);
 });
 
DWObject.Viewer.on('dblclick',function(index){
 console.log(index);
 });

DWObject.Viewer.on('contextmenu',function(index){
 console.log(index);
 });

DWObject.Viewer.on('mousemove',function(index){
 console.log(index);
 });
```

## pageAreaSelected

**Syntax**

``` typescript
/**
 * This event is triggered when user selects an area (draws a rectangle) or move a selected area on an image in Dynamic Web TWAIN viewer.
 * @argument index The index of the current image.
 * @argument rect Some attribute values of the selected area.
 */
on('pageAreaSelected', 
     function(
     index：string, 
     rect: rect
     )=> void
): void; 

interface rect{ 
     /**
     * The index of the selected area. The index is 0-based. This is useful when you have multiple selected areas on one image.
     */
    areaIndex: number;
     /**
     * The x-coordinate of the upper-left corner of the rectangle.
     */
    x: number;
     /**
     * The y-coordinate of the upper-left corner of the rectangle.
     */
    y: number;
     /**
     * The width of the selected area.
     */
    width: number;
     /**
     * The height of the selected area.
     */
    height: number;
```

**Example**

``` typescript
DWObject.Viewer.on('pageAreaSelected', function(sImageIndex, rect){console.log(sImageIndex)});  
 
DWObject.Viewer.off('pageAreaSelected'); 
```

## pageAreaUnselected

**Syntax**

``` typescript
/**
 * This event is triggered when user deselects an area (clicks outside of the drawn rectangle) on an image in Dynamic Web TWAIN viewer.
 * @argument index The index of the current image.
 */
on('pageAreaUnselected', 
     function(
     index：string) => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.on('pageAreaUnselected',function(sImageIndex){console.log('The selected area on the image with index '+ sImageIndex + ' has been deselected');});
 
DWObject.Viewer.off('pageAreaUnselected'); 
```

## pageRendered

**Syntax**

``` typescript
/**
 * This event is triggered when new images have been acquired/loaded into the viewer.
 * @argument index The index of the current image.
 */
on('pageRendered', 
     function(
     index：string) => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.on("pageRendered",function(index){
 console.log(index);
 }); 

DWObject.LoadImage("1.png");  //It will trigger pageRendered event
```

## resize

**Syntax**

``` typescript
/**
 * This event is triggered when width & height of the viewer has been changed.
 * @argument iwidth The new width of the viewer.
 * @argument iheight The new height of the viewer.
 */
 on('resize', 
     function(
     iwidth：number;
     iheight：number;) => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.on("resize",function(iwidth,iheight){
 console.log(iwidth);
 }); 
```

## topPageChanged

**Syntax**

``` typescript
/**
 * This event is triggered when the top image currently displayed in Dynamic Web TWAIN viewer changes.
 * @argument index The index of the current image.
 */
on('topPageChanged', 
     function(
     index：string) => void
): void; 
```

**Example**

``` typescript
DWObject.Viewer.on("topPageChanged",function(index){
 console.log(index);
 }); 

**Usage notes**

The returned value index means the index of the top image.

This event is only effective when the view mode is not -1 * -1.