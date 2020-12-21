---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API - Appendix
keywords: Dynamic Web TWAIN, Documentation, API Appendix
breadcrumbText: API Appendix
description: Dynamic Web TWAIN SDK Documentation API Appendix Page
---

# API Appendix

## Viewer related API changes in version 16.2

### For the Camera add-on

* New APIs in v16.2 replace old APIs in v16.1-, all old APIs are deleted.

| v16.2 | v16.1- |
|-:|-:|
| [ `Addon.Camera.closeVideo()` ] | `Viewer.closeVideo()` |
| [ `Addon.Camera.off()` ] | `Viewer.off()` |
| [ `Addon.Camera.on("video-closed")` ] | `Viewer.on("video-closed")` |
| [ `Addon.Camera.on("video-error")` ] | `Viewer.on("video-error")` |
| [ `Addon.Camera.showVideo()` ] | `Viewer.showVideo()` |

### For the Viewer

* New APIs in v16.2 replace old APIs in v16.1-, all old APIs are deprecated.

| v16.2 | v16.1- |
|-:|-:|
| `Viewer.background` | `BackgroundColor` |
| `Viewer.bind()` , `Viewer.show()` , `Viewer.hide()` | `BindViewer()` |
| `Viewer.cursor` | `MouseShape` |
| `Viewer.fitWindow()` | `FitWindowType` , `IfFitWindow` |
| `Viewer.height` | `Height` |
| `Viewer.ifAutoScroll` | `IfAutoScroll` |
| `Viewer.on("click", callback)` | `RegisterEvent("OnMouseClick", callback)` |
| `Viewer.on("contextmenu", callback)` | `RegisterEvent("OnMouseRightClick", callback)` |
| `Viewer.on("dblclick", callback)` | `RegisterEvent("OnMouseDoubleClick", callback)` |
| `Viewer.on("mousemove", callback)` | `RegisterEvent("OnMouseMove", callback)` |
| `Viewer.on("pageAreaSelected", callback)` | `RegisterEvent("OnImageAreaSelected", callback)` |
| `Viewer.on("pageAreaUnselected", callback)` | `RegisterEvent("OnImageAreaDeSelected", callback)` |
| `Viewer.on("topPageChanged", callback)` | `RegisterEvent("OnTopImageInTheViewChanged", callback)` |
| `Viewer.pageMargin ` | `ImageMargin` |
| `Viewer.selectedPageBorder` | `SelectionImageBorderColor` |
| `Viewer.selectionRectAspectRatio` | `SelectionRectAspectRatio` |
| `Viewer.setSelectedAreas()` | `SetSelectedImageArea()` |
| `Viewer.showPageNumber` | `ShowPageNumber` |
| `Viewer.unbind()` | `UnbindView()` |
| `Viewer.width ` | `Width` |
| `Viewer.zoom` | `Zoom` |
| `ViewerEvent.imageX` | `MouseX` |
| `ViewerEvent.imageY` | `MouseY` |

> NOTE
>  
> `ViewerEvent.imageX` and `ViewerEvent.imageY` are only available as the first argument in callback functions for the mouse events "click", "dblclick", "contextMenu" and "mousemove".

* The following APIs are new in v16.2

[ `Viewer.acceptDrop` ]
[ `Viewer.allowSlide` ]
[ `Viewer.clearSelectedAreas()` ]
[ `Viewer.createThumbnailViewer()` ]
[ `Viewer.border` ]
[ `Viewer.first()` ]
[ `Viewer.getUISettings()` ]
[ `Viewer.gotoPage()` ]
[ `Viewer.idPostfix` ]
[ `Viewer.innerBorder` ]
[ `Viewer.last()` ]
[ `Viewer.next()` ]
[ `Viewer.on("pageRendered", callback)` ]
[ `Viewer.on("resize", callback)` ]
[ `Viewer.previous()` ]
[ `Viewer.render()` ]
[ `Viewer.resetUISettings()` ]
[ `Viewer.selectedAreaBorderColor` ]
[ `Viewer.selectedPageBackground` ]
[ `Viewer.singlePageMode` ]

* The following APIs in v16.2 are improved based on old APIs in v16.1-.

  + [`Viewer.setViewMode()`]

    It also accepts the values "-1, -1" which is equivalent to setting `Viewer.singlePageMode` to `true` .

  + [`Viewer.updateUISettings()`]

* The following APIs are also deprecated in v16.2

  + [`SetViewMode()`]

    Use Viewer.setViewMode() instead.

* The following APIs in v16.1- are removed

  + `Viewer.bOnlyShowThumbnailsView`
  + `Viewer.cursorOverThumbnailsView`
  + `Viewer.bindCustomElement()`
  + `Viewer.showCustomElement()`
  + `Viewer.hideCustomElement()`
  + `Viewer.toggleCustomElement()`
  + `Viewer.setSelectedImageArea()`
  + `Viewer.zoomIn()`
  + `Viewer.zoomOut()`

* The following APIs in v16.1- are implemented differently in v16.2  
  + `BindViewer()` with two parameters
  + `UpdateViewer()`

  The two methods above were used to set the size of the viewer or to show the thumbnail viewer. In v16, 2, different APIs are used as shown below:
  

``` javascript
  /* Set the size of the viewer */
  DWObject.Viewer.height = 800;
  DWObject.Viewer.width = 600;
  /* Create a thumbnail viewer, note that this viewer can be hidden or disposed */
  var objThumbnailViewer = DWObject.Viewer.createThumbnailViewer(thumbnailViewerSettings);
  objThumbnailViewer.show();
  //objThumbnailViewer.hide();
  //objThumbnailViewer.dispose();
  /* updateViewMode() is used to change only the view mode of the thumbnail viewer */
  objThumbnailViewer.updateViewMode(viewMode: ViewMode);
  /* The following two are used to hook or unhook events to the thumbnail viewer */
  objThumbnailViewer.on()
  objThumbnailViewer.off()
```

  + `ShowImageEditor()`

  While this method still works, it's deprecated and the alternative is shown in the code below

``` javascript
  /* The image editor is now created on the fly and can be hidden or disposed */
  var objImageEditor = DWObject.Viewer.createImageEditor(editorSettings);
  objImageEditor.show();
  objImageEditor.hide();
  objImageEditor.dispose();
```

  + `Viewer.bindCustomElement()`
  + `Viewer.showCustomElement()`
  + `Viewer.hideCustomElement()`
  + `Viewer.toggleCustomElement()`

  As already mentioned, these four methods are removed and the alternative is shown in the code below

``` javascript
  var objCustomElement = DWObject.Viewer.createCustomElement(document.getElementById("divCustomElement"));
  objCustomElement.show();
  objCustomElement.hide();
  objCustomElement.dispose();
```
