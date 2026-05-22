---
description: この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。
keywords: ID サービス
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 87%

---

# resetBeforeVersion{#resetbeforeversion}

この設定を使用すると、更新対象の ID サービスのバージョンに基づいて、孤立したり古くなったりした Experience Cloud ID（ECID）を消去できます。

`resetBeforeVersion` 変数の値として ID サービスのバージョンを指定すると、クライアント側 ID から古い ECID が消去されます。

セッションのタイムアウトなど、条件によっては、ID サービスでサーバーサイド ID が正常に取得されずに、クライアントサイド ID が生成されることがあります。 この場合、孤立したクライアントサイド ID は ID サービスによって追跡されますが、ドメイン間で追跡したり、他のソリューションと適切に同期したりすることはできません。 この動作では、現在の AMCV Cookie のバージョンと `resetBeforeVersion` の値が比較されます。 Cookieが存在しないか、Cookieのバージョンが最新リリースされたバージョンの`resetBeforeVersion`より古い（古い）場合、AMCV Cookieが削除され、ID サービスは新しいECIDをリクエストします。

ブラウザーにサードパーティ Demedex Cookie がある訪問者の場合、ECID が、この Demedex Cookie の UUID を使用して適切に生成されたかどうかがチェックされます。 そのチェックの結果が真であるとわかった場合、新しい ECID は同じになり、訪問者は新規と見なされます。 何らかの理由で、クリアされる ECID が demdex Cookie を使用して生成されなかった場合、または demdex Cookie がない場合、訪問者は新しい ECID を受け取り、新規と見なされます。

**構文：** `resetBeforeVersion = "3.3"`

**コードサンプル**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
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

