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
* [getUISettings()](#getuisettings)
* [gotoPage()](#gotopage)
* [hide()](#hide)
* [last()](#last)
* [next()](#next)
* [off()](#off)
* [on()](#on)
* [previous()](#previous)
* [render()](#render)
* [resetUISettings()](#resetuisettings)
* [setButtonClass()](#setbuttonclass)
* [setSelectedAreas()](#setselectedAreas)
* [setViewMode()](#setviewmode) 
* [show()](#show)
* [unbind()](#unbind)
* [updateUISettings()](#updateuisettings)

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
