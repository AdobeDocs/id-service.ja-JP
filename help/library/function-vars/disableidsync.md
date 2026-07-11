---
description: ID 同期を無効にするブール型のフラグ（オプション）。
keywords: 訪問者 ID サービス
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
TQID: https://experienceleague.adobe.com/ltW03vCXP9-8G7kJ8KwKOwAOgrsxkTxSoGzImR7dax0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 40
ht-degree: 100%

---

# disableIdSyncs{#disableidsyncs}

ID 同期を無効にするブール型のフラグ（オプション）。

>[!NOTE]
>
>この設定は従来 `idSyncDisableSyncs` でしたが、2018 年 1 月 18 日（PT）の v3.0 リリースで `disableIdSyncs` に名称変更されました。

**構文：** `disableIdSyncs: true|false`（デフォルトは `false` です。）

**コードサンプル**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

