---
description: Experience Cloud ID サービス地域 ID を返します。地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。
keywords: ID サービス
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Experience Cloud ID サービス地域 ID を返します。地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。

**構文：** ` var *`変数名`* = visitor.getLocationHint()`

地域 ID と対応する場所の一覧は、[DCS 地域 ID、場所、ホスト名](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ja)を参照してください。

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
