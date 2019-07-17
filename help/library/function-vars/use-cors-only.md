---
description: ブラウザーがExperience Cloud IDサービスからリソースをリクエストする方法を制御するブール型のフラグ。
keywords: ID サービス
seo-description: ブラウザーがExperience Cloud IDサービスからリソースをリクエストする方法を制御するブール型のフラグ。
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

ブラウザーがExperience Cloud IDサービスからリソースをリクエストする方法を制御するブール型のフラグ。

**構文：**`useCORSOnly: true|false`（デフォルトは `false` です。）

**概要**

`false` に設定すると、ブラウザーは、CORS または JSONP を使用してリソースチェックを実行します。ただし、ID サービスは常に、最初に CORS を使用してリソースをリクエストしようとします。CORS をサポートしていない古いブラウザーでは、JSONP に切り替わります。CORS のみを使用するようにブラウザーを強制する必要がある場合、`useCORSOnly:true` 関数呼び出しで `Visitor.getInstance` を設定します。

>[!IMPORTANT]
>
>厳格なセキュリティ要件がある場合は、`Set useCORSOnly: true` を設定します。すべての訪問者が CORS をサポートするブラウザーを使用しているという確信がある場合にのみ、このモードを有効にする必要があります。ユーザーエクスペリエンスは、CORS をサポートしていないブラウザーの影響を受けません。ただし、CORS をサポートしていないブラウザーは、[!DNL Adobe Experience Cloud] を使用してリソースをリクエストしたり、データを交換したりできません。

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

