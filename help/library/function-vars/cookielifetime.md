---
description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
keywords: ID サービス
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。

デフォルトでは、[!DNL Experience Cloud] ID サービス Cookie は、24 ヶ月後に有効期限が切れます。この間隔を秒単位で設定します。

**構文：** ` cookieLifetime: *`全期間（秒単位）`*`

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
