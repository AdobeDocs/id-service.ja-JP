---
description: この設定を使用すると、更新中の訪問者ID サービスのバージョンに基づいて、孤立したECIDまたは古いECID （ECID）をクリアできます。
keywords: 訪問者 ID サービス
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 41%

---

# resetBeforeVersion{#resetbeforeversion}

この設定を使用すると、更新中の訪問者ID サービスのバージョンに基づいて、孤立したECIDまたは古いECID （ECID）をクリアできます。

訪問者ID サービスのバージョンを`resetBeforeVersion`変数の値として指定すると、クライアント側のIDから古いECIDがクリアされます。

セッションのタイムアウトなどの一部の条件では、訪問者ID サービスがサーバーサイド IDを正常に取得せずに、クライアントサイド IDが生成されることがあります。 このような場合、孤立したクライアントサイド IDは、ドメイン間で追跡されたり、他のソリューションと適切に同期したりすることなく、訪問者ID サービスによって追跡されます。 この動作では、現在の AMCV Cookie のバージョンと `resetBeforeVersion` の値が比較されます。 Cookieが存在しないか、Cookieのバージョンが最新リリースされたバージョンの`resetBeforeVersion`よりも古い場合、AMCV Cookieは削除され、訪問者ID サービスは新しいECIDをリクエストします。

ブラウザーにサードパーティ Demedex Cookie がある訪問者の場合、ECID が、この Demedex Cookie の UUID を使用して適切に生成されたかどうかがチェックされます。 そのチェックの結果が真であるとわかった場合、新しい ECID は同じになり、訪問者は新規と見なされます。 何らかの理由で、クリアされる ECID が demdex Cookie を使用して生成されなかった場合、または demdex Cookie がない場合、訪問者は新しい ECID を受け取り、新規と見なされます。

**構文：** `resetBeforeVersion = "3.3"`

**コードサンプル**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

