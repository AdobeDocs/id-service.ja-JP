---
description: Experience Cloud ID サービスが実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。
keywords: ID サービス
seo-description: Experience Cloud ID サービスが実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105- b377- d9b4d247a0f8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Experience Cloud ID サービスが実装される前に s_vi Cookie に保存されていた従来の Analytics ID を返します（存在する場合）。訪問者に Analytics ID が割り当てられたことがない場合は、空の文字列を返します。

**構文** `var analyticsID = visitor.getAnalyticsVisitorID()`

この関数は、通常、訪問者 ID を読み取る必要があるカスタムソリューションで使用されます。標準の実装では使用されません。`getAnalyticsVisitorID` は、[!DNL Analytics] ID を読み取ってシステムまたはアプリケーションに送信するコールバック関数とも連携します。

**サンプルコード**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>お客様 [!DNL Analytics] の場合は、 [!DNL Analytics] IDをチェックして関数に送信します。例えば、hidden フォーム要素の訪問者 ID を、データ挿入 API を使用するサーバー側のアプリケーションに渡す場合に、両方の識別子が必要になります。この場合、訪問者IDと [!DNL Experience Cloud][!DNL Analytics] 訪問者IDを収集して返します。[getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md)を参照してください。

**「aid」パラメーターは従来の値です**

`aid` パラメーターは異なる 2 つの条件セット下で、クエリ文字列内で使用されます。

**例 1**

`aid` パラメーターは次の場合に、クエリ文字列内で使用されます。

* [!DNL Experience Cloud] IDサービスが正しくデプロイされている。
* サイトに訪問しているユーザーの [!DNL Analytics]s_vi Cookie[ に既に ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) ID が保存されている場合。

**例 2**

組織が猶予期間 `aid` を [使用している場合、IDサービスを完全に実装](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) する前に、クエリ文字列にパラメーターが表示されます。サイトを訪問しているユーザーが新規であり、猶予期間を使用していない場合、訪問者は `mid` （ [!DNL Experience Cloud] ID）パラメーターを取得します。

>[!MORE_ LIKE_ THIS]
>
>* [Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

