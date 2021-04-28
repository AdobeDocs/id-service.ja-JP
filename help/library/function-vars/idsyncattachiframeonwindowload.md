---
description: Experience Cloud Identity Service が ID 同期 iFrame を読み込む方法を制御するブール型フラグです（オプション）。
keywords: ID サービス
seo-description: Experience Cloud Identity Service が ID 同期 iFrame を読み込む方法を制御するブール型フラグです（オプション）。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad {#idsyncattachiframeonwindowload}

Experience Cloud Identity Service が ID 同期 iFrame を読み込む方法を制御するブール型フラグです（オプション）。

**構文：** ` `idSyncAttachIframeOnWindowLoad= true false``（デフォルトは `false`。）

`idSyncAttachIframeOnWindowLoad: true` の場合、ID サービスは、ウィンドウの読み込み時に ID 同期 iFrame を読み込みます。デフォルトでは、ID サービスは、ウィンドウの読み込み時ではなく、可能な限り早く ID 同期 iFrame を読み込みます。

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
