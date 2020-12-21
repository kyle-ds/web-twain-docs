---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting General Failure 
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, General Failure
breadcrumbText: General Failure
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors General Failure Page
---

# Handling Errors

## General failure

* Symptom

When you try scanning an image with Dynamic Web TWAIN, you may receive the error message "General failure" in the ErrorString property.

* Cause

The problem occurs when the source (scanner) is *not* disabled completely after a scanning session or the source is currently unavailable.

* Resolution

You can set [IfDisableSourceAfterAcquire]({{site.info}}api/WebTwain_Acquire.html#ifdisablesourceafteracquire) to `true` . It must be set before the call to [SelectSource]({{site.info}}api/WebTwain_Acquire.html#selectsource)

``` javascript
function AcquireImage() {
    DWObject.IfDisableSourceAfterAcquire = true;
    DWObject.SelectSource();
    DWObject.OpenSource();
    DWObject.AcquireImage();
}
```