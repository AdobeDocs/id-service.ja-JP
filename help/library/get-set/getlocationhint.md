---
description: Experience Cloud ID サービス地域 ID を返します。 地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。 Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。
keywords: ID サービス
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Experience Cloud ID サービス地域 ID を返します。 地域 ID（またはロケーションヒント）は、特定の ID サービスデータセンターの地理的場所を示す数値識別子です。 Audience Manager へのサーバー側 API 呼び出しをおこなうには、地域 ID が必要です。

**構文：** `var *`変数名`* = visitor.getLocationHint()`

地域 ID と対応する場所の一覧は、[DCS 地域 ID、場所、ホスト名](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=ja)を参照してください。

**コードサンプル**

ロケーションヒント関数は、AMCV Cookie から地域 ID を読み取ります。 地域 ID が既に AMCV Cookie に設定されている場合、即座にコールバックが発生します。 地域 ID が設定されていない場合、関数は、地域 ID がコールバックに渡されるまで、サーバーからの応答を待ちます。 コードは、以下の例のようになります。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

