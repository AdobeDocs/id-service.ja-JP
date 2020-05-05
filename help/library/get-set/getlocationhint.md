---
description: Experience Cloud Identity Service 地域 ID を返します。地域ID（またはロケーションヒント）は、特定のIDサービスデータセンターの地理的な場所を示す数値識別子です。 オーディエンスマネージャーに対するサーバー側API呼び出しを行うには、地域IDが必要です。
keywords: ID Service
seo-description: Experience Cloud Identity Service 地域 ID を返します。地域ID（またはロケーションヒント）は、特定のIDサービスデータセンターの地理的な場所を示す数値識別子です。 オーディエンスマネージャーに対するサーバー側API呼び出しを行うには、地域IDが必要です。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getLocationHint{#getlocationhint}

Experience Cloud Identity Service 地域 ID を返します。地域ID（またはロケーションヒント）は、特定のIDサービスデータセンターの地理的な場所を示す数値識別子です。 オーディエンスマネージャーに対するサーバー側API呼び出しを行うには、地域IDが必要です。

**構文：** ` var *`変数名`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**コードサンプル**

ロケーションヒント関数は、AMCV cookieから地域IDを読み取ります。 地域IDが既にAMCV cookieに設定されている場合は、即座にコールバックが発生します。 地域IDが設定されていない場合、関数は、地域IDをコールバックに渡す前に、サーバーからの応答を待ちます。 コードは、以下の例のようになります。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

