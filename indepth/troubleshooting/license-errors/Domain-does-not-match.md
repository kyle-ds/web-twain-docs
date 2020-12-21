---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN Troubleshooting The Current Product Key Does Not Match The Domain
keywords: Dynamic Web TWAIN, Documentation, Troubleshooting, License Errors, Domain Does Not Match
breadcrumbText: Domain Doesn't Match
description: Dynamic Web TWAIN SDK Documentation Troubleshooting License Errors Domain Doesn't Match Page
---


# Handling Errors

## The current product key does not match the domain

* Symptom

When you visit a `DWT` application , you may be met with this error message.

* Cause

To protect your license, you can bind it to your domain. When you do this, you must make sure your application is deployed to the bound domain, otherwise you will receive the error.

* Resolution

Make sure you deployed the application to the domain bound to your license or add the domain to your license bindings by contacting [Dynamsoft Support]({{site.about}}getsupport.html).