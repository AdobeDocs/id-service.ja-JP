---
description: ID 同期を無効にするブール型のフラグ（オプション）。
keywords: ID サービス
seo-description: ID 同期を無効にするブール型のフラグ（オプション）。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15- bcf5- f0869763a32e
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

ID 同期を無効にするブール型のフラグ（オプション）。

>[!NOTE]
>
>この設定は、 `idSyncDisableSyncs` v3.0の2018年1月18日リリースで変更 `disableIdSyncs` され、名前が変更されました。

**構文:**`disableIdSyncs: true|false` （デフォルトは `false`、です）。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

