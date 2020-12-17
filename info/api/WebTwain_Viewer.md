---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API Reference - Viewer APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Viewer APIs
breadcrumbText: Viewer
description: Dynamic Web TWAIN SDK Documentation API Reference Viewer APIs Page
---

# `WebTwain.Viewer`
> For WebTwain instances

**Methods**

* [BindViewer()](#bindviewer)
* [UnbindView()](#unbindviewer)
* [UpdateViewer()](#updateviewer)

**Properties**

* [BackgroundColor](#backgroundcolor) 
* [SelectionImageBorderColor](#selectionimagebordercolor)
* [FitWindowType](#fitwindowtype) 
* [IfFitWindow](#iffitwindow)
* [Height](#height) 
* [Width](#width)
* [IfAutoScroll](#ifautoscroll) 
* [ShowPageNumber](#showpagenumber)
* [MouseX](#mousex)
* [MouseY](#mousey)
* [ImageMargin](#imagemargin) 
* [MouseShape](#mouseshape)
* [SelectionRectAspectRatio](#selectionrectaspectratio) 
* [Zoom](#zoom)

**Events**

* [OnMouseClick](#onmouseclick) 
* [OnMouseDoubleClick](#onmousedoubleclick)
* [OnMouseMove](#onmousemove) 
* [OnMouseRightClick](#onmouserightclick)
* [OnImageAreaSelected](#onimageareaselected)
* [OnImageAreaDeSelected](#onimageareadeselected)

> For the WebTwain. Viewer interface

**Methods**

* [setViewMode()](#setviewmode) 
* [updateUISettings()](#updateuisettings)
* [setButtonClass()](#setbuttonclass) 
* [setSelectedImageArea()](#setselectedimagearea)
* [zoomIn()](#zoomin) 
* [zoomOut()](#zoomout)
* [bindCustomElement](#bindcustomelement) 
* [showCustomElement](#showcustomelement)
* [hideCustomElement](#hidecustomelement)
* [toggleCustomElement](#togglecustomelement)
* [on()](#on)

**Properties**

* [cursor](#cursor)
* [bOnlyShowThumbnailsView](#bonlyshowthumbnailsview)
* [cursorOverThumbnailsView](#cursoroverthumbnailsview)

**Events**

* [video-closed](#vidoe-closed)
* [video-error](#vidoe-error)

---

## BindViewer

**Syntax**

``` typescript
/**
 * Create a Dynamsoft Viewer instance and bind it to the WebTwain instance.
 * @param elementId Specify an HTML element to create the viewer.
 * @param config Configuration of the viewer.
 */
BindViewer(
    elementId: string,
    config ? : BasicViewerConfig
): boolean;

interface BasicViewerConfig {
    /**
     * Specify the size of the viewer.
     */
    Height: number | string;
    Width: number | string;
    /**
     * Set up the content view.
     */
    view: ContentView;
}

interface ContentView {
    /**
     * Whether to show the content view or not.
     * If set to false, then only thumbnails view is shown.
     */
    bShow: boolean;
    /**
     * Specify the width of the major content view.
     */
    Width: number | string;
}
```

---

## UpdateViewer

**Syntax**

``` typescript
/**
 * Update the viewer with the new configuration.
 * @param config Configuration of the viewer.
 */
UpdateViewer(config: BasicViewerConfig): boolean;

interface BasicViewerConfig {
    /**
     * Specify the size of the viewer.
     */
    Height: number | string;
    Width: number | string;
    /**
     * Set up the content view.
     */
    view: ContentView;
}

interface ContentView {
    /**
     * Whether to show the content view or not.
     * If set to false, then only thumbnails view is shown.
     */
    bShow: boolean;
    /**
     * Specify the width of the major content view.
     */
    Width: number | string;
}
```

---

## UnbindViewer

**Syntax**

``` typescript
/**
 * Unbind and destroy the viewer.
 */
UnbindViewer(): boolean;
```

**Example**

``` javascript
/**
 * Create a viewer in the div with the Id 'dwtcontrolContainer'. Use default settings.
 */
DWObject.BindViewer('dwtcontrolContainer');
```

Example configurations of the viewer, note that both hardcoded numbers (of pixels) and percentages can be used to specify the size of the viewer.

``` javascript
DWObject.UpdateViewer({
    Height: 600, // 600 pixels high
    Width: 500, // 500 pixels wide
    view: {
        bShow: true, // Show the content view
        Width: 300 // The content view is 300 pixels wide
    }
});
```

``` javascript
DWObject.UpdateViewer({
    Height: "60%", // 60% height of the parent element
    Width: "50%", // 50% width of the parent element
    view: {
        bShow: true, // Show the content view
        Width: "80%" // 80% width of the viewer
    }
});
```

---

## BackgroundColor

**Syntax**

``` typescript
/**
 * Return or set the background colour | image of the viewer.
 */
BackgroundColor: number | string;
```

**Usage notes**

The number that represents the number comes in the form of 0xRRGGBB. For example, the following code sets the background to pure Green.

``` javascript
DWObject.BackgroundColor = 0x00ff00;
```

You can also set an image as the background by its URL. For example

``` javascript
DWObject.BackgroundColor = "url(https://demo.dynamsoft.com/dwt/Images/icon-dwt.svg)";
```

---

## SelectionImageBorderColor

**Syntax**

``` typescript
/**
 * Return or set the border colour for selected image(s).
 */
SelectionImageBorderColor: number;
```

**Usage notes**

By default the colour is white (0xffffff). The byte-ordering of the 24-bit RGB value is **RRGGBB**. RR represents red, GG represents green and BB represents blue.

---

## FitWindowType

**Syntax**

``` typescript
/**
 * Return or set how the image is fit in the viewer.
 */
FitWindowType: number;
```

**Usage notes**

This API only works if the view mode of the viewer is set to -1 by -1.

The allowed values of `FitWindowType` are

* `0` : Default value, try to fit the image both horizontally and vertically.
* `1` : Fit the image vertically.
* `2` : Fit the image horizontally.

---

## IfFitWindow

**Syntax**

``` typescript
/**
 * Return or set whether to fit the current image to the viewer window.
 */
IfFitWindow: boolean;
```

**Usage notes**

This API only works if the view mode of the viewer is set to -1 by -1.

The default value of `IfFitWindow` is true.

---

## Height

**Syntax**

``` typescript
/**
 * Return or set the height of the viewer.
 */
Height: number | string;
```

---

## Width

**Syntax**

``` typescript
/**
 * Return or set the width of the viewer.
 */
Width: number | string;
```

**Usage notes**

Example values

* `number`

``` javascript
DWObject.Height = 600; // 600 pixels high
DWObject.Width = 500; // 500 pixels wide
```

* `string`

``` javascript
DWObject.Height = "600px"; // 600 pixels high
DWObject.Width = "500px"; // 500 pixels wide
```

Or

``` javascript
DWObject.Height = "50%"; // 50% of the parent element's height
DWObject.Width = "50%"; // 50% of the parent element's width
```

---

## MouseX

**Syntax**

``` typescript
/**
 * Return the horizontal coordinate of the mouse.
 */
readonly MouseX: number;
```

---

## MouseY

**Syntax**

``` typescript
/**
 * Return the vertical coordinate of the mouse.
 */
readonly MouseY: number;
```

**Usage notes**

The coordinates are meaured in pixels and is based on the original size of the image.

**Example**

``` javascript
DWObject.RegisterEvent('OnMouseMove',
    function() {
        console.log("X: " + DWObject.MouseX + " Y: " + DWObject.MouseY);
    }
);
```

---

## SelectionRectAspectRatio

**Syntax**

``` typescript
/**
 * Change the position of an image in the buffer.
 * @param from Specify the original position by index.
 * @param to Specify the target position by index.
 */
SelectionRectAspectRatio: number;
```

---

## MouseShape

**Syntax**

``` typescript
/**
 * Return or set the shape of the cursor.
 */
MouseShape: boolean;
```

**Usage notes**

Unlike [cursorOverThumbnailsView](#cursoroverthumbnailsview), this property set the shape of the cursor that's effective both on the thumbnails view and the content view.

The allowed values are

* `true` : The default value. The shape is "hand".
* `false` : The shape is "crosshair" and you can drag to select an area on the image.

**Example**

``` javascript
DWObject.MouseShape = false;
```

---

## IfAutoScroll

**Syntax**

``` typescript
/**
 * Return or set whether the thumbnails view scrolls when new images come in.
 */
IfAutoScroll: boolean;
```

**Usage notes**

By default, the property is `true` which means the thumbnails view will scroll to show the latest acquire/loaded images.

Set it to `false` if you want the view to keep showing the same images even as more images are acquire/loaded.

**Example**

``` javascript
DWObject.IfAutoScroll = false;
```

---

## ShowPageNumber

**Syntax**

``` typescript
/**
 * Return or set whether to show the page numbers.
 */
ShowPageNumber: boolean;
```

**Usage notes**

The page number indicates the order of the images.

When the viewmode is -1 * -1, page numbers will be hidden.

---

## ImageMargin

**Syntax**

``` typescript
/**
 * Return or set the margin between images (in pixels).
 */
ImageMargin: number;
```

**Usage notes**

The image margin is only effective when the view mode is not 1 * 1 nor -1 * -1.

---

## Zoom

**Syntax**

``` typescript
/**
 * Return or set the zoom factor.
 */
Zoom: number;
```

**Usage notes**

The zoom factor is only effective when the view mode is -1 * -1. 

When you set the property and the view mode is -1 * -1, the view will zoom in or out.

---

## OnMouseClick

## OnMouseDoubleClick

## OnMouseMove

## OnMouseRightClick

**Syntax**

``` typescript
/**
 * A built-in callback triggered when the mouse click | double-click | right-click on an image or move over it.
 * @argument index Specify the image.
 */
RegisterEvent('OnMouseClick', function(index: number) {}): boolean;
RegisterEvent('OnMouseDoubleClick', function(index: number) {}): boolean;
RegisterEvent('OnMouseRightClick', function(index: number) {}): boolean;
RegisterEvent('OnMouseMove', function(index: number) {}): boolean;
```

---

## OnImageAreaSelected

**Syntax**

``` typescript
/**
 * A built-in callback triggered when a rectangle is selected on an image in the buffer.
 * @argument index Specify the image.
 * @argument left, top, right, bottom: Return the coordinates of the rectangle.
 * @argument rectangleIndex The index of the rectangle
 */
RegisterEvent('OnImageAreaSelected',
    function (index: number,
        left: number, top: number,
        right: number, bottom: number,
        rectangleIndex: number
    ) {}
): boolean;
```

---

## OnImageAreaDeSelected

**Syntax**

``` typescript
/**
 * A built-in callback triggered when selected rectangles are cleared.
 * @argument index Specify the image.
 */
RegisterEvent('OnImageAreaDeSelected',
    function (index: number) {}
): boolean; 
```

---

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

---

## setSelectedImageArea

**Syntax**

``` typescript
/**
 * Select a rectangular area on the specified image.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param width Specify the rectangle (the width).
 * @param height Specify the rectangle (the height).
 */
setSelectedImageArea(
    left: number,
    top: number,
    width: number,
    height: number
): boolean;
```

**Usage notes**

The coordinates are based on the size of the original image (instead of the size of the viewer).

**Example**

``` javascript
DWObject.Viewer.setSelectedImageArea(50, 50, 200, 200);
```

---

## setButtonClass

**Syntax**

``` typescript
/**
 * Set the CSS class name of the specified button.
 * @param name Specify the button.
 * @param className Specify the CSS class name.
 */
setButtonClass(
    name: string,
    className: string
): boolean;
```

**Usage notes**

Use this method to fine-tune the buttons in the viewer with CSS.

**Example**

``` javascript
DWObject.Viewer.setButtonClass("crop", "CropClass");
```

---

## zoomIn

**Syntax**

``` typescript
/**
 * Zoom in by 6/5.
 */
zoomIn(): boolean;
```

---

## zoomOut

**Syntax**

``` typescript
/**
 * Zoom out by 5/6.
 */
zoomOut(): boolean;
```

---

## bindCustomElement

**Syntax**

``` typescript
/**
 * Bind a custom element to the viewer to add extra features.
 * @param Id Specify the element by its Id.
 * @param priority Specify the importance of the element.
 * @param fullScreen Whether to show the element full-screen.
 */
bindCustomElement(
    Id: string,
    priority: number,
    fullScreen: boolean
): boolean;
```

**Usage notes**

You can put any information in the custom element. Once bound, it'll be managed by the viewer.

---

## unBindCustomElement

**Syntax**

``` typescript
/**
 * Unbind a custom element from the viewer.
 * @param Id Specify the element by its Id.
 */
unBindCustomElement(
    Id: string
): boolean;
```

---

## showCustomElement

**Syntax**

``` typescript
/**
 * Show the custom element.
 * @param name Specify the element by its Id.
 */
showCustomElement(Id: string): boolean;
```

---

## hideCustomElement

**Syntax**

``` typescript
/**
 * Hide the custom element.
 * @param name Specify the element by its Id.
 */
hideCustomElement(Id: string): boolean;
```

---

## toggleCustomElement

**Syntax**

``` typescript
/**
 * Show or hide the custom element.
 * @param name Specify the element by its Id.
 */
toggleCustomElement(Id: string): boolean;
```

---

## on

**Syntax**

``` typescript
/**
 * Specify an event listener for the specified built-in viewer event.
 * @param name Specify the event
 * @param callback The event listener
 */
on(name: string, callback: () => void): boolean;
```

---

## video-closed

**Syntax**

``` typescript
/**
 * This event is triggered when the video is closed.
 */
on("video-closed", callback: () => void): boolean;
```

---

## video-error

**Syntax**

``` typescript
/**
 * This event is triggered when the video playing operation. throws out an error.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
on("video-error", callback: (errorCode, errorString) => void): boolean;
```

---

## bOnlyShowThumbnailsView

**Syntax**

``` typescript
/**
 * Whether to only show the thumbnails view.
 */
bOnlyShowThumbnailsView: boolean;
```

---

## cursorOverThumbnailsView

**Syntax**

``` typescript
/**
 * Set the shape of the cursor over the thumbnails view.
 */
cursorOverThumbnailsView: string;
```

---

## updateUISettings

**Syntax**

``` typescript
/**
 * Update the viewer with detailed configuration.
 * @param config Specify the detailed configuration.
 */
updateUISettings(config: IViewerConfig): boolean;

interface ViewerConfig {
    /**
     * Specify which components are shown.
     */
    component ? : {
        header ? : boolean;
        topMenu ? : boolean;
        asideMenu ? : boolean;
        bottomMenu ? : boolean;
    };
    group ? : {
            global ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'header'
                sequence ? : number
            },
            tabName ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'header'
                sequence ? : number
            },
            viewerCorner ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'header'
                sequence ? : number
            },
            viewMenuBlock ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenu'
                sequence ? : number
            },
            viewMenu ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenu'
                sequence ? : number
            },
            topMenuRight ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenu'
                sequence ? : number
            },
            pager ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'bottomMenu'
                sequence ? : number
            },
            viewChange ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'header'
                sequence ? : number
            }
        },
        buttons ? : {
            // loadImage button
            loadImage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewerCorner'
                iconClass ? : string, // Example: 'icon-file'
                sequence ? : number,
                onButtonClick ? : string // Example: onLoadImage'
            },
            currentTab ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'tabName',
                sequence ? : number
            },
            // panelChange button (thumbnail, dir tree, tags)
            panelChange ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'global'
                iconClass ? : string, // Example: 'icon-list'
                sequence ? : number,
                onButtonClick ? : string // Example: onPanelChange'
            },
            // readDirection change button (vertical ,horizontal)
            readDirection ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'global'
                iconClass ? : string, // Example: 'icon-readType'
                sequence ? : number,
                onButtonClick ? : string // Example: onReadDirection'
            },
            // readDirection change button (vertical ,horizontal)
            blank1 ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'global'
                sequence ? : number
            },
            // flip button
            flip ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-flip'
                sequence ? : number,
                onButtonClick ? : string // Example: onFlip'
            },
            // mirror button
            mirror ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-mirror'
                sequence ? : number,
                onButtonClick ? : string // Example: onMirror'
            },
            // rotate button
            rotate ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-rotateLeft'
                sequence ? : number,
                onButtonClick ? : string // Example: onRotate'
            },
            // rotateAll button
            rotateAll ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-rotateAll'
                sequence ? : number,
                onButtonClick ? : string // Example: onRotateAll'
            },
            // crop button
            crop ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-crop'
                sequence ? : 5,
                onButtonClick ? : string // Example: onCrop'
            },
            // wipe button
            wipe ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-wipe'
                sequence ? : 6,
                onButtonClick ? : string // Example: onWipe'
            },
            // undo button
            undo ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-undo'
                sequence ? : 7,
                onButtonClick ? : string // Example: onUndo'
            },
            // redo button
            redo ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-redo'
                sequence ? : 8,
                onButtonClick ? : string // Example: onRedo'
            },
            // magnifyCanvas button
            zoomIn ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-magnifyImage'
                sequence ? : 9,
                onButtonClick ? : string // Example: onZoomIn'
            },
            // shrinkCanvas button
            zoomOut ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-shrinkImage'
                sequence ? : 10,
                onButtonClick ? : string // Example: onZoomOut'
            },
            // reset button
            reset ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewMenu'
                iconClass ? : string, // Example: 'icon-reset'
                sequence ? : 11,
                onButtonClick ? : string // Example: onReset'
            },
            // remove button
            remove ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenuRight'
                iconClass ? : string, // Example: 'icon-delete'
                sequence ? : number,
                onButtonClick ? : string // Example: onRemove'
            },
            // print button
            print ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenuRight'
                iconClass ? : string, // Example: 'icon-print'
                sequence ? : number,
                onButtonClick ? : string // Example: onPrint'
            },
            // save button
            save ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'topMenuRight'
                iconClass ? : string, // Example: 'icon-save'
                sequence ? : number,
                onButtonClick ? : string // Example: onSave'
            },
            // firstPage button
            firstPage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'pager'
                iconClass ? : string, // Example: 'icon-pageStart'
                sequence ? : number,
                onButtonClick ? : string // Example: onFirstPage'

            },
            // previousPage button
            previousPage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'pager'
                iconClass ? : string, // Example: 'icon-pagePre'
                sequence ? : number,
                onButtonClick ? : string // Example: onPreviousPage'
            },
            //pagination show
            pagination ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'pager'
            },
            // nextPage button
            nextPage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'pager'
                iconClass ? : string, // Example: 'icon-pageNext'
                sequence ? : number,
                onButtonClick ? : string // Example: onNextPage'
            },
            // lastPage button
            lastPage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'pager'
                iconClass ? : string, // Example: 'icon-pageEnd'
                sequence ? : 5,
                onButtonClick ? : string // Example: onLastPage'
            },
            // autoFit button
            autoFit ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewChange'
                iconClass ? : string, // Example: 'icon-autoFit'
                sequence ? : number,
                onButtonClick ? : string // Example: onAutoFit'
            },
            // fitHeight button
            fitHeight ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewChange'
                iconClass ? : string, // Example: 'icon-fitHeight'
                sequence ? : number,
                onButtonClick ? : string // Example: onFitHeight'
            },
            // fitWidth button
            fitWidth ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewChange'
                iconClass ? : string, // Example: 'icon-fitWidth'
                sequence ? : number,
                onButtonClick ? : string // Example: onFitWidth'
            },
            // fullScreenToWebPage button
            fullPage ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewChange'
                iconClass ? : string, // Example: 'icon-fullWeb'
                sequence ? : number,
                onButtonClick ? : string // Example: onFullPage'
            },
            // fullScreenToDevice
            fullScreen ? : {
                visibility ? : boolean,
                location ? : string, // Example: 'viewChange'
                iconClass ? : string, // Example: 'icon-fullDevice'
                sequence ? : number,
                onButtonClick ? : string // Example: onFullScreen'
            }
        },
        tipsConfig ? : {
            loadImage ? : string, // Example 'loadImage'
            panelChange ? : string, // Example 'panelChange'
            readDirection ? : string, // Example 'readDirection'
            flip ? : string, // Example 'flip'
            mirror ? : string, // Example 'mirror'
            rotate ? : string, // Example 'rotate'
            rotateAll ? : string, // Example 'rotateAll'
            crop ? : string, // Example 'crop'
            wipe ? : string, // Example 'wipe'
            undo ? : string, // Example 'undo'
            redo ? : string, // Example 'redo'
            zoomIn ? : string, // Example 'zoomIn'
            zoomOut ? : string, // Example 'zoomOut'
            reset ? : string, // Example 'reset'
            remove ? : string, // Example 'remove'
            print ? : string, // Example 'print'
            save ? : string, // Example 'save'
            firstPage ? : string, // Example 'firstPage'
            previousPage ? : string, // Example 'previousPage'
            pagination ? : string, // Example 'pagination'
            nextPage ? : string, // Example 'nextPage'
            lastPage ? : string, // Example 'lastPage'
            autoFit ? : string, // Example 'fitWindow'
            fitHeight ? : string, // Example 'fitHeight'
            fitWidth ? : string, // Example 'fitWidth'
            fullPage ? : string, // Example 'fullPage'
            fullScreen ? : string, // Example 'fullScreen'
        },
        content ? : {
            visibility ? : boolean,
            besides ? : {
                visibility ? : boolean,
                sequence ? : number
            },
            viewPort ? : {
                visibility ? : boolean,
                sequence ? : number
            },
            allImage ? : {
                visibility ? : boolean,
                displayName ? : string // Example: 'All Images'
            }
        },
        thumbnail ? : {
            visibility ? : boolean,
            iconClass ? : string // Example: 'icon-thumbnail'
            selectedBorderColor ? : string // Example: 'red'
            selectedBackgroundColor ? : string // Example: 'rgb(127, 133, 251)'
            imageBackgroundColor ? : string // Example: 'transparent'
            imageBorderColor ? : string // Example: 'gray'
            hoverBackgroundColor ? : string // Example: '#c4faf8'
            hoverBorderColor ? : string // Example: 'yellow'
            blockBackgroundColor ? : string // Example: 'pink'
            backgroundColor ? : string // Example: 'rgba(67, 66, 70, 1)'
            imageSpace ? : number, // Example: 10
            showPageNumber ? : boolean,
            showThumbnailControl ? : boolean,
            mouseShape ? : string // Example: 'pointer'
        },
        tree ? : {
            visibility ? : boolean,
            iconClass ? : string // Example: 'icon-tree',
            selectedColor ? : string // Example: '#0000ff',
            goToThumbnail ? : boolean
        },
        tag ? : {
            visibility ? : boolean,
            iconClass ? : string // Example: 'icon-tags',
            selectedColor ? : string // Example: '#0000ff',
            goToThumbnail ? : boolean,
            displayMode ? : string // Example: ''// icon or text
        },
        cropStyle ? : {
            ratios ? : any, // Example [[1, 1], [3, 2], [4, 3], [5, 4], [7, 5], [16, 9]],
            cropMask ? : boolean,
            cropBar ? : boolean
        },
        buttonResize ? : {
            ifResize ? : boolean,
            maxSize ? : number, // Example: 26,
            minSize ? : number, // Example: 14
        },
        skinColor ? : {
            topMenuBackground ? : string // Example: '#000000'
            asideBackground ? : string // Example: '#ffffff'
            canvasBackground ? : string // Example: 'rgba(67,66,70,1)'
            bottomMenuBackground ? : string // Example: '#000000'
        },
        presetMode ? : string // Example: 'basic'
    theme ? : string // Example: 'basic'
}
```

> The following APIs are under development for version 16.2

## width

**Syntax**

``` typescript
/**
 * Return or set the width of the viewer.
 */ 
Viewer.width: number | string;
```

**Usage Notes**

If a number is assigned, it means that number of pixels (px). If a string is assigned, it is either a fixed size like "500px" or a dynamic size like "50%" which follows standard CSS rules.
 
**Example**

``` javascript
DWObject.Viewer.width = 270;
DWObject.Viewer.width = "270px";
DWObject.Viewer.width = "100%";
```

## height

**Syntax**

``` typescript
/**
 * Return or set the height of the viewer.
 */ 
Viewer.height: number | string;
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
