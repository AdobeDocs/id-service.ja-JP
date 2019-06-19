---
description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
keywords: ID サービス
seo-description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625- ac3f-69ac259377a3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。

デフォルトで [!DNL Experience Cloud] は、IDサービスcookieは24ヶ月後に期限切れになります。この間隔を秒単位で設定します。

**構文:**` cookieLifetime: *`秒単位のライフタイム`*`

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

