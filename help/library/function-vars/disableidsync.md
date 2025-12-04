---
description: ID 同期を無効にするブール型のフラグ（オプション）。
keywords: ID サービス
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# disableIdSyncs{#disableidsyncs}

ID 同期を無効にするブール型のフラグ（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisableSyncs` でしたが、2018 年 1 月 18 日（PT）の v3.0 リリースで `disableIdSyncs` に名称変更されました。

**構文：** `disableIdSyncs: true|false`（デフォルトは `false` です。）

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

