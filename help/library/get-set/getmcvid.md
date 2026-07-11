---
description: getMarketingCloudVisitorIDはECIDを返します。
keywords: 訪問者 ID サービス
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorIDはECIDを返します。

**構文：** `var *`変数名`* = visitor.getMarketingCloudVisitorID()`

この方法は通常、訪問者 ID の読み取りを必要とするカスタムソリューションで使用されます。 標準の実装では使用されません。 `getMarketingCloudVisitorID`は、コールバック関数を使用してAnalytics IDを読み取り、システムまたはアプリケーションに取り込むこともできます。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Analyticsのお客様の場合は、Analytics IDを確認して関数に送信します。 例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。 この場合、ECIDとAnalyticsの訪問者IDを収集して返す必要があります。 [Analytics 訪問者 ID の取得](../../library/get-set/getanalyticsvisitorid.md)を参照してください。

