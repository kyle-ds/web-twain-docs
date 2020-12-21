---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting Sequence Error
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, Common Errors, Sequence Error
breadcrumbText: Sequence Error
description: Dynamic Web TWAIN SDK Documentation Troubleshooting Common Errors Sequence Error Page
---

# Handling Errors

## Sequence error

* Symptom

	When you fail to acquire images from your scanner, you may get this error.

* Cause

	The problem happens when the process does not occur in the correct TWAIN sequence.

* Resolution

	Check if you followed the acquisition sequence to get images from your device. For example, some methods and properties, like the [PixelType]({{site.info}}api/WebTwain_Acquire.html#pixeltype) property, can only be used after calling the [OpenSource()]({{site.info}}api/WebTwain_Acquire.html#opensource) method. Please check the TWAIN State Transition Diagram below for more information

![TWAIN State Transition]({{site.assets}}imgs/TWAIN-State-Transition.png)