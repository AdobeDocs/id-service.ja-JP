---
description: エクスペリエンスプラットフォームIDサービスがID同期iFrameを読み込む方法を制御するブール型のフラグ。
keywords: ID サービス
seo-description: エクスペリエンスプラットフォームIDサービスがID同期iFrameを読み込む方法を制御するブール型のフラグ。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

エクスペリエンスプラットフォームIDサービスがID同期iFrameを読み込む方法を制御するブール型のフラグ。

**構文:**` `idSyncAttachIframeOnWindowLoad= true| false「（デフォルトは `false`.）

`idSyncAttachIframeOnWindowLoad: true` の場合、ID サービスは、ウィンドウの読み込み時に ID 同期 iFrame を読み込みます。デフォルトでは、ID サービスは、ウィンドウの読み込み時ではなく、可能な限り迅速に ID 同期 iFrame を読み込みます。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```
