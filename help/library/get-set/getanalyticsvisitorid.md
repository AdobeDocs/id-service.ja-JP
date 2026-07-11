---
description: 訪問者ID サービスが実装される前にs_vi Cookieに保存されていた従来のAnalytics ID （存在する場合）を返します。 訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。
keywords: 訪問者 ID サービス
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 46%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

訪問者ID サービスが実装される前にs_vi Cookieに保存されていた従来のAnalytics ID （存在する場合）を返します。 訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。

**構文** `var analyticsID = visitor.getAnalyticsVisitorID()`

この関数は、通常、訪問者 ID を読み取る必要があるカスタムソリューションで使用されます。 標準の実装では使用されません。 `getAnalyticsVisitorID`は、コールバック関数を使用してAnalytics IDを読み取り、システムまたはアプリケーションに取り込むこともできます。

**サンプルコード**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Analyticsのお客様の場合は、Analytics IDを確認して関数に送信します。 例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。 この場合、ECIDとAnalyticsの訪問者IDを収集して返す必要があります。 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) を参照してください。

**「aid」パラメーターは従来の値です**

`aid` パラメーターは異なる 2 つの条件セット下で、クエリ文字列内で使用されます。

**例 1**

`aid` パラメーターは次の場合に、クエリ文字列内で使用されます。

* 訪問者ID サービスが正しくデプロイされます。
* サイトを訪問しているユーザーは、既存のAnalytics IDを[s_vi Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=ja#section-5d50a078de444d12b7d927d68ff3b679?lang=ja)に保存しています。

**例 2**

組織が訪問者ID サービスを完全に実装する前に[猶予期間](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration)を使用している場合、クエリ文字列に`aid` パラメーターが表示されます。 サイトを訪問しているユーザーが新しいユーザーで、猶予期間を使用していない場合、訪問者は`mid` （ECID） パラメーターを取得します。

>[!MORELIKETHIS]
>
>* [Analytics の cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=ja)

