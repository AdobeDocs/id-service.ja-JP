---
description: エクスペリエンスプラットフォームIDサービス地域IDを返します。地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。
keywords: ID サービス
seo-description: エクスペリエンスプラットフォームIDサービス地域IDを返します。地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7- d270-4a5c- a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getLocationHint{#getlocationhint}

エクスペリエンスプラットフォームIDサービス地域IDを返します。地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。

**構文:**` var *`変数名`* = visitor.getLocationHint()`

地域 ID と対応する場所の一覧は、[DCS 地域 ID、場所、ホスト名](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html)を参照してください。

**コードサンプル**

ロケーションヒント関数は、AMCV Cookie から地域 ID を読み取ります。地域 ID が既に AMCV Cookie に設定されている場合、即座にコールバックが発生します。地域 ID が設定されていない場合、関数は、地域 ID がコールバックに渡されるまで、サーバーからの応答を待ちます。コードは、以下の例のようになります。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

