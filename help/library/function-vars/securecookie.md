---
description: AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。
keywords: ID サービス
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 93
ht-degree: 100%

---

# secureCookie{#securecookie}

AMCV Cookie に「Secure」属性を追加するブール型フラグ（オプション）。

この設定属性は、`visitorAPI` バージョン 3.3.0 で使用できます。

>[!NOTE]
>
>`SecureCookie` 設定は、セキュリティで保護されていないドメインで機能しません。その結果、セキュリティで保護されていないプロトコルを使用する訪問について MID 値が返されない可能性があります。 `secureCookie` を `true` に設定する必要があるのは、すべてのページおよびサブドメインでセキュリティで保護されたプロトコルが常に使用されていることを確認できた場合のみです。

**構文：** `secureCookie: true | false`（デフォルト）

**コードサンプル**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

