---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting You Have Exceeded The Number Of OCR Attempts Allowed By The Current License
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, License Errors, OCR License Exceeded
breadcrumbText: OCR License Exceeded
description: Dynamic Web TWAIN SDK Documentation Troubleshooting License Errors OCR License Exceeded Page
---

# Handling Errors

## You have exceeded the number of OCR attempts allowed by the current license

* Symptom

When you use the OCRPro addon, you may receive this error message returned by the member method GetErrorString() of the OCRResult class.

* Cause

It is a license issue. The OCRPro licenses are yearly licenses and each license has a limitation on the number of pages allowed to be OCR'ed. The SDK will throw this error when the limitation is reached.

* Solution

The license quota has been used up and extra quota needs to be purchased. Contact [Dynamsoft Support]({{site.about}}getsupport.html) for any assistance.