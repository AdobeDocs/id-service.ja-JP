---
description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
keywords: ID サービス
seo-description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '64'
ht-degree: 100%

---

# cookieLifetime {#cookielifetime}

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
