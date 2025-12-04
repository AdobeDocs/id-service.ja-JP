---
description: ブラウザーが Experience Cloud ID サービスからリソースをリクエストする方法を制御するブール型フラグです（オプション）。
keywords: ID サービス
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 87%

---

# useCORSOnly{#usecorsonly}

ブラウザーが Experience Cloud ID サービスからリソースをリクエストする方法を制御するブール型フラグです（オプション）。

**構文：** `useCORSOnly: true|false`（デフォルトは `false` です。）

**概要**

`false` に設定すると、ブラウザーは、CORS または JSONP を使用してリソースチェックを実行します。ただし、ID サービスは常に、最初に CORS を使用してリソースをリクエストしようとします。 CORS をサポートしていない古いブラウザーでは、JSONP に切り替わります。CORS のみを使用するようにブラウザーを強制する必要がある場合、`useCORSOnly:true` 関数呼び出しで `Visitor.getInstance` を設定します。

>[!IMPORTANT]
>
>厳格なセキュリティ要件がある場合は、`Set useCORSOnly: true` を設定します。このモードは、すべての訪問者が CORS をサポートするブラウザーを使用していると確信できる場合にのみ有効にしてください。 ユーザーエクスペリエンスは、CORS をサポートしないブラウザーの影響を受けません。 ただし、CORS をサポートしていないブラウザーは、[!DNL Adobe Experience Cloud] を使用してリソースをリクエストしたり、データを交換したりできません。

**コードサンプル**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

