---
description: ブラウザーが訪問者ID サービスにリソースをリクエストする方法を制御する、オプションのブール値フラグ。
keywords: 訪問者 ID サービス
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 46%

---

# useCORSOnly{#usecorsonly}

ブラウザーが訪問者ID サービスにリソースをリクエストする方法を制御する、オプションのブール値フラグ。

**構文：** `useCORSOnly: true|false`（デフォルトは `false` です。）

**概要**

`false` に設定すると、ブラウザーは、CORS または JSONP を使用してリソースチェックを実行します。 ただし、訪問者ID サービスは常にCORSを使用してリソースをリクエストしようとします。 CORS をサポートしていない古いブラウザーでは、JSONP に切り替わります。 CORS のみを使用するようにブラウザーを強制する必要がある場合、`useCORSOnly:true` 関数呼び出しで `Visitor.getInstance` を設定します。

>[!IMPORTANT]
>
>厳格なセキュリティ要件がある場合は、`Set useCORSOnly: true` を設定します。 すべての訪問者がCORSをサポートするブラウザーを使用していることを確信している場合にのみ、このモードを有効にする必要があります。 ユーザーエクスペリエンスは、CORS をサポートしないブラウザーの影響を受けません。 ただし、CORS サポートを持たないブラウザーは、リソースをリクエストしたり、Adobe CX Enterpriseとデータを交換したりすることはできません。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

