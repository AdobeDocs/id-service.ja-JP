---
description: この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。
keywords: ID サービス
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
TQID: https://experienceleague.adobe.com/EBAkG9W3VE4p7Xd5NkegOtFDNo6qBOKrKRaBUYwwJog
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 51
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

この変数を使用すると、AMCV Cookie のデフォルトのライフタイム間隔を上書きできます。

デフォルトでは、[!DNL Experience Cloud] ID サービス Cookie は、24 ヶ月後に有効期限が切れます。 この間隔を秒単位で設定します。

**構文：** `cookieLifetime: *`全期間（秒単位）`*`

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

