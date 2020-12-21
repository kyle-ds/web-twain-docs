---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting Source Is Connected To The Maximum Supported Number Of Applications
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, Source Connected To Maximum
breadcrumbText: Source Connected To Maximum
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors Source Connected To Maximum Page
---

# Handling Errors

## Source is connected to the maximum supported number of applications

* Symptom

	When you try to acquire images, you may get this error.

* Cause

	The problem may occur when the source is **not** disabled completely after a transfer ends or is used by other applications.

* Resolution
  + Check whether another application is using the source. If yes, close it and try again.
  + Set [IfDisableSourceAfterAcquire]({{site.info}}api/WebTwain_Acquire.html#ifdisablesourceafteracquire) to `true` and use [CloseSource()]({{site.info}}api/WebTwain_Acquire.html#closesource) to make sure that the source is closed after a scanning session.

	``` javascript
	function btnScan_onclick() {
	    DWObject.RegisterEvent("OnPostAllTransfers", function() {
	        DWObject.CloseSource();
	    });
	    DWObject.SelectSource();
	    DWObject.CloseSource(); //close source before open
	    DWObject.OpenSource();
	    DWObject.IfDisableSourceAfterAcquire = true; //close source after acquiring
	    DWObject.AcquireImage();
	}
	```  
	Reboot your device.