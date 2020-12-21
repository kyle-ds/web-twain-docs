---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN API Reference - Global APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Global APIs
breadcrumbText: Global
description: Dynamic Web TWAIN SDK Documentation API Reference Global APIs Page
---

# `Dynamsoft.WebTwainEnv`

> Global properties and functions.

``` typescript
interface Dynamsoft.WebTwainEnv {
    readonly ActiveXVersion: string;
    readonly JSVersion: string;
    readonly PdfVersion: string;
    readonly ServerLinuxVersionInfo: string;
    readonly ServerMacVersionInfo: string;
    readonly ServerVersionInfo: string;
    /**
     * Whether to create a WebTwain instance automatically.
     */
    AutoLoad: boolean;
    ContainerMap: object;
    /**
     * Define the Id and UI of the WebTwain instances.
     */
    Containers: Container[];
    Host: string; //"local.dynamsoft.com"
    IfAddMD5InUploadHeader: boolean;
    IfDisableDefaultSettings: boolean;
    IfUseActiveXForIE10Plus: boolean;
    readonly inited: boolean;
    ProductKey: string;
    ResourcesPath: string;
    UseLocalService: boolean;
    UseDefaultInstallUI: boolean;
    
    // Functions
    CreateDWTObject(
        ContainerId: string, 
        host?: string, 
        port?: string | number, 
        portSSL?: string | number, 
        asyncSuccessFunc: function (DWObject: WebTwain) {}, 
        asyncFailureFunc: function (errorString: string) {}
    ): void;
    CreateDWTObjectEx(
        dwtInitialConfig: DWTInitialConfig,                 
        asyncSuccessFunc: (DWObject: WebTwain) => {},                   
        asyncFailureFunc: (errorString: string) => {}
    ): void;
    DeleteDWTObject(Id?: string): boolean;
    GetWebTwain(ContainerId?: string): WebTwain;
    GetWebTwainEx(WebTwainId: string): WebTwain;
    Load(): void;
    Unload(): void;
    RemoveAllAuthorizations: function () {};
    OnWebTwainNotFound: function () {};
    OnWebTwainPostExecute: function () {};
    OnWebTwainPreExecute: function () {};
    OnWebTwainReady: function () {};
    OnWebTwainWillInit: function () {};
    UseDefaultViewer: boolean;
    CustomizableDisplayInfo: CustomizableDisplayInfo;
    WasmConfig: WasmConfig;
}
interface CustomizableDisplayInfo {
  // Specify the source of the loader bar.
  loaderBarSource: string;
}
interface WasmConfig {
  maxHeapSize: number;
  fetchOptions: fetchOptions;
}
interface fetchOptions {
  headers: HeadersInit;
  mode: RequestMode;
  credentials: RequestCredentials;
}
```

## Options

### `Containers`

An array of `Container` definitions that specifies the UI elements for `WebTwain` instances. The `Container` interface is defined below

``` typescript
interface Container {
    WebTwainId: string, // Id of the WebTwain instance
    ContainerId?: string, // Id of the element
    Width?: string | number, // Width of the element
    Height?: string | number // Height of the element
}
```

### `IfAddMD5InUploadHeader`

Whether or not an md5 header `dwt-md5` should be included in HTTP upload requests. Note that this header is not a standard header and may be deemed invalid on some web servers.
  
The default value is `false` .

### `ProductKey`

Sets or returns the product key for the library. A product key is required to enables certain modules of the library.

### `ResourcesPath`

Sets or returns where the library looks for resources files including service installers, CSS, etc.
  

### `UseLocalService`

Sets or returns whether to use the service or use WASM only. This property can be changed at runtime (but not recommended) and affects `WebTwain` instances created after the change.

The default value is `true` .

## Functions

### `CreateDWTObject()`

Creates a new `WebTwain` instance that listens to the specified host & ports. An UI element specified by the parameter `ContainerId` which is typically a <div> is required. The library will generate a UI and bind it to this element.

### `CreateDWTObjectEx()`

Creates a new UI-less `WebTwain` instance. This instance will be uniquely identified by the parameter `WebTwainId` .

``` typescript
interface DWTInitialConfig {
  WebTwainId: string;
  Host ? : string;
  Port ? : string;
  PortSSL ? : string;
  UseLocalService?: boolean;
}
```

### `DeleteDWTObject()`

Delete the `WebTwain` instance specified by `Id` which can either be a `ContainerId` or a `WebTwainId` .

### `GetWebTwain()`

Gets an `WebTwain` instance by its `ContainerId` .

### `GetWebTwainEx()`

Gets an `WebTwain` instance by its `WebTwainId` .

### `Load()`

Initiates the library. If there are predefined `Containers` , one `WebTwain` instance will be created for each `Container` .

### `RegisterEvent()`

Registers an environmental event. Typically the event is `OnWebTwainReady` which is triggered when the initialization completes.

### `Unload()`

Destroys all `WebTwain` instances and cuts off the connection to the Dynamsoft Service.

### `UseDefaultViewer`

Whether to use the built-in viewer.

### `CustomizableDisplayInfo`

#### `loaderBarSource`

Specify the source of the loader bar.
  
### `WasmConfig`

#### `maxHeapSize`

Specify the maximum memory allowed to be used by the library when it's in WASM-mode. By default, it's 200 (MB).

#### `fetchOptions`

* `headers`

A Headers object, an object literal, or an array of two-item arrays to set request's headers. Check out [HeadersInit](https://microsoft.github.io/PowerBI-JavaScript/modules/_node_modules_typedoc_node_modules_typescript_lib_lib_dom_d_.html#headersinit).

* `mode`

A string to indicate whether the request will use CORS, or will be restricted to same-origin URLs. Sets request's mode. Check out [RequestMode](https://microsoft.github.io/PowerBI-JavaScript/modules/_node_modules_typedoc_node_modules_typescript_lib_lib_dom_d_.html#requestmode).

* `credentials`

A string indicating whether credentials will be sent with the request always, never, or only when sent to a same-origin URL. Sets request's credentials. Check out [RequestCredentials](https://microsoft.github.io/PowerBI-JavaScript/modules/_node_modules_typedoc_node_modules_typescript_lib_lib_dom_d_.html#requestcredentials).